NLP is a specialized area in AI that exclusively deals with processing of Natural language including understanding, generating text such as individual characters, words, paragraphs, documents such as whole of Wikipedia. 

# Table of Contents
  * [Basic NLP concepts](#concepts)
  * [AI Basics](#AIBasics)
  * [How NLP fits in AI](#NLPandAI) 
  * [Modelling using RNN, LSTMs](#ModellingBasic)
  * [Advanced Modelling (Transformers)](#ModellingAdvances)
  * [Generative AI](#GENAI)


# Basic NLP Concepts <a id="concepts"></a>

Language is **symbolic and discrete**. Both characters and words are discrete symbols. The basic elements of written language are characters. Characters form words that in turn denote objects, concepts, events, actions, and ideas. For instance, words such as "hamburger" or "pizza" each evoke in us a certain mental representations, but they are also distinct symbols, *whose meaning is external to them and left to be interpreted in our heads.*

While in Computer Vision (CV) or Speech Processing, basic building blocks are continuous in nature, allowing, for exanple, to move from a colorful image  to a gray-scale one using a simple mathematical operation, or to compare two different colors based on their inherent properties such as hue and intensity. This can not be done easily with words - *there is no simple operation that will allow us to move from the word "red" to the word "pink" without using a large lookup table or dictionary*.

Language is also compositional: letters form words, and words form phrases and sentences. In order to interpret a text, we thus need to work beyond the level of letters and words, and look at long sequences of words such as sentences, or even complete documents.

The combination of the above properties leads to data sparseness. The way in which words (discrete symbols) can be combined to form meanings is practically infinite. The number of possible valid sentences is tremendous: we could never hope to enumerate all of them. 

#### Challenges for computational approaches when dealing with NLP:
  1. Language is discrete.
  2. Language is sparse.
  3. Language is compositional.
  4. Language is ambiguous and often consists of variable number of inputs.

###  *"Main idea is to convert discrete words into continuous numeric representation"*

#### Solution - [Neural Networks](NNetwork.md) with an Embedding layer: 

- Major component in neural networks for language is the use of an embedding layer, a mapping of discrete symbols to continuous vectors in a relatively low dimensional space.
- When embedding words, they transform from being isolated distinct symbols into mathematical objects that can be operated on. This capability alleviates to some extent the **discreteness and data-sparsity** problems.

Before understanding the *embedding* concept, it is key to understand various pre-dating concepts to represent the discrete language into continuous numerical vector that can also help in reflecting various linguistic properties of the text in form of feature vector:
- **Bag of words**: This technique represents text by counting the frequency of words in a document, without considering the order or structure of the words. Each document is represented as a vector where each dimension corresponds to a unique word, and the value in each dimension represents the frequency of that word in the document.
- **TF-IDF**:TF-IDF is another representation technique that weighs the importance of words in a document relative to a collection of documents (corpus). It considers term frequency within a document and the inverse document frequency across the entire corpus to assign weights to words.
- **N-grams**: Besides words, one may also look at consecutive pairs or triplets of words. These are called ngrams.
- **Lemma**: The lemma of a word can be ambiguous, and lemmatizing is more accurate when the word is given in context.
- **Stemming**: A stemmer maps sequences of words to shorter sequences, based on some language-specific heuristics, such that different inflections will map to the same sequence.
- **POS Tags**: These represent the *inferred linguistic properties* of words, sentences, and documents. For e.g., we could look at the *part-of-speech* tag (POS) of a word within a document (Is it a noun, a verb, adjective, or a determiner?).
- **Named-Entity-Recognition**: Knowing that a document contains the word *Paris* is an indication toward the document being in the *TRAVEL* category, and the same holds for the word *Hilton*. Such special words have **NER** tags assigned to them.
- **One-hot-Encoding**: Each dimension corresponds to a unique feature and the resulting feature vector can be thought of as a combination of high-dimensional indicator vectors in which a single dimension has a value of 1 and all others have a value of 0. For instance, given a vocabulary of 40,000 items, a document of 20 words will be represented by a very sparse 40,000-dimensional vector in which at most 20 dimensions have non-zero values.
   - Each dimension represent a feature.
   - Feature combinations receive their own dimensions.
   - Feature values are binary
   - Dimensionality is very high.
   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/04115cc3-ed9e-4d0f-8e07-93e5c74b7a7e)



- **Embeddings**:
  *<ins>Basic idea is that "words should be encoded into a low-dimensional and dense vector"</ins>*

    ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/42801c45-bc3d-42d6-b72c-93d1470d3b1d)

- Each core feature is embedded into a ‘d’ dimensional space and represented as a vector in that space.
- The dimension ‘d’ is usually much smaller than the number of features, i.e., each item in a vocabulary of 40,000 items (encoded as 40,000-dimensional one-hot vectors) can be represented as a 100 or 200-dimensional vector.
- The embeddings (the vector representation of each core feature) are treated as parameters of the network and are trained like the other parameters of the function f.
  
  ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/b6c81d6a-d33c-44d5-8c25-7d6fd0ce604c)

  Feed-forward networks assume a fixed dimensional input. This can easily accommodate the case of a feature-extraction function that extracts a fixed number of features: each feature is represented as a vector, and the vectors are concatenated. This   
  way, each region of the resulting input vector corresponds to a different feature.

  But what if the features are variable? For e.g., suppose features are words themselves such as in a document classification task.

  We thus need to represent an unbounded number of features using a fixed-size vector. One way of achieving this is through a so-called continuous bag of words (CBOW ) representation.

  ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/dd87ee1e-5a15-4a17-9148-edfbecbf8f29)

  ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/f3643bc9-0222-403a-8944-df8e6dc23ab4)

   <ins>FineTuning of Pre-trained Embedding matrix for the task</ins>:
   - Consider an embedding matrix E ∈ R<sup>|V|xd</sup> associating words from vocabulary V with d-dimensional vectors. *"A common approach would be to treat **E** as model parameters, and change it with rest of the network."*

   <ins>How these **"pre-trained embeddings"** are obtained?</ins>:
   - Given a training corpus, we prepare a list of N (input_word, output_word).
  - Objective Function: Maximize probability of all the output words given the corresponding input words.
  - This method is called **word2vec**.
  - Usually 2 **word2vec** approaches are common:
        - SkipGram : Given a specific word, predict its nearby word (probability output).
        - CBOW : Given a context, predict its target word.
    
   Here’s how it works:

   1. <ins>**Initialize the Embedding Layer**</ins>: The weights of the embedding layer are initialized with the pre-trained word embeddings. This means that, initially, the embedded representation of a word is its pre-trained word vector.

   2. <ins>**Forward Propagation**</ins>: During training, each word in the input data is represented as a one-hot vector. This one-hot vector is input to the embedding layer, which uses it to look up the corresponding embedded    representation in the embedding matrix. This embedded representation is then passed through the rest of the network.

  3. <ins>**Backward Propagation and Weight Update**</ins>: The network makes a prediction, and this is compared to the true output. The difference between the predicted and true output is calculated using a loss function. This loss is then back-propagated through the network to update the weights. The weights in the embedding layer (i.e., the word embeddings) are updated in this process.

  4. <ins>**Iterate**</ins>: Steps 2 and 3 are repeated for each batch of data. Over multiple iterations (epochs), the model learns to adjust the weights of the embeddings along with the weights of the other layers in the network to minimize the loss function.

*<ins>In the case of Word2Vec, the model learns word embeddings from scratch. It doesn’t start with pre-existing word embeddings. Instead, it initializes with random vectors and then adjusts these vectors to minimize the prediction error in its task (either predicting the context words given a target word for Skip-Gram, or predicting the target word given the context words for CBOW).</ins>*

#### <ins>How to use pre-trained embeddings for **Sentiment Analysis** task? (w/o embedding layer)</ins>

Pre-trained word embeddings can be very useful for a sentiment analysis task. Here’s a general approach:

1. <ins>**Prepare your data**</ins>: For sentiment analysis, you’ll typically have a dataset of text samples and their corresponding sentiment labels. First, you’ll need to preprocess your text data by tokenizing the text into words, handling punctuation, and so forth.

2. <ins>**Convert words to vectors**</ins>: Next, for each word in your text data, you’ll look up its corresponding vector in the pre-trained word embeddings. This will give you a sequence of vectors for each text sample.

3. <ins>**Aggregate the vectors**</ins>: Since your model will likely require a fixed-size input, you’ll need to convert your sequence of vectors into a single vector. A common way to do this is by **averaging all the vectors together**, but there are also other methods like using **[RNNs, LSTMs](NNetwork.md), or [Transformers](Transformers.md)**.

4. <ins>**Train your model**</ins>: Now that your text data is represented as fixed-size vectors, you can input these vectors into your model. You’ll train your model to predict the sentiment label given the input vector.

#### <ins>How to use pre-trained embeddings for **Sentiment Analysis** task? (with embedding layer)</ins>

When you have an embedding layer as part of your model, the input to the model is typically the integer-encoded representation of your text data, not the one-hot encoded vectors.

Here’s how it works:

1. <ins>**Tokenization**</ins>: You first convert your text data into a list of tokens (words).

2. <ins>**Integer Encoding**</ins>: Each unique token (word) in your text data is assigned a unique integer. This process creates a dictionary that maps words to integers. You then use this dictionary to convert your list of tokens into a list of integers.

3. <ins>**Input to Embedding Layer**</ins>: These integer-encoded tokens are then fed into the embedding layer of the model. The embedding layer uses these integers to look up the embedding vector for each word.

So, in this setup, the one-hot encoding step is skipped, and words are directly mapped to their integer indices. These indices are used to look up the embeddings in the embedding layer.

#### <ins> Contextual embeddings (trained and used at the same time!) </ins>

1. <ins>**Tokenization**</ins>: The text is broken down into tokens (words or subwords, depending on the model).

2. <ins>**Integer Encoding**</ins>: Each token is mapped to a unique integer, similar to the process I described earlier.

3. <ins>**Model Processing**</ins>: The integer-encoded tokens are input to the pre-trained model, which processes them using layers of transformers (in the case of BERT or GPT) or a combination of convolutional neural networks (CNNs) and long short-term memory (LSTM) networks (in the case of ELMo).

4. <ins>**Output**</ins>: The output is a set of vectors, where each vector corresponds to a token in the input. These vectors are the contextual embeddings. They represent the meaning of each word in the context of the given sentence.

5. <ins>**Sequence Processing**</ins>: The sequence of embeddings is then processed by another part of your model. This could be a Recurrent Neural Network (RNN), a Transformer, or even a simpler model like a Convolutional Neural Network (CNN) or a Feed Forward Neural Network (FFNN). This part of the model is responsible for “understanding” the sequence of embeddings and making a prediction based on them.

6. <ins>**Sentiment Prediction**</ins>: The final layer of your model is a dense layer with one neuron for each sentiment category (e.g., positive, negative, neutral). This layer makes the final sentiment prediction based on the processed embeddings.

```

# # Load pre-trained BERT model and tokenizer
model_name = 'bert-base-uncased'
tokenizer = BertTokenizer.from_pretrained(model_name)
model = BertForSequenceClassification.from_pretrained(model_name, num_labels=num_labels)
```

When you load a pre-trained BERT model, it includes several components:

1. <ins>**Embedding Layer**</ins>: This is the first layer of the model, and it’s responsible for converting input tokens into vectors. This layer includes pre-trained embeddings for each token in the BERT tokenizer’s vocabulary.

2. <ins>**Transformer Layers**</ins>: These are the main body of the model. They take the vectors from the embedding layer and transform them through a series of self-attention mechanisms and feed-forward networks. The weights in these layers are also pre-trained.

3. <ins>**Classification Layer**</ins>: This is the final layer of the model, and it’s responsible for making predictions based on the output of the Transformer layers. In the BertForSequenceClassification model, this is a simple linear layer that outputs a logit for each class in your classification task.

So, when you load a pre-trained BERT model, you’re actually loading pre-trained embeddings along with pre-trained Transformer layers. These components are then fine-tuned on your specific task (sentiment analysis in this case).


# AI Basics <a id="AIBasics"></a>

The training data is assumed to be constant while weights of a Network are said to be variable.

- Machine Learning.
- Supervised algorithms:
  - Linear Regression
  - Logistic Regression
  - SVM
  - Decision Tree
  - K-Nearest Neighbour
  - Random Forest
  - XG-Boost
 - UnSupervised algorithms:
   - CLustering
      - Agglomerative/Hierarchical
      - Point Assignment:
         - K-Means clustering
      - Density Based
   - PCA
   - Autoencoders
  - Evaluation metrics:
     - Precision, Recall, Accuracy, ROC AUC Curve, Precision-Recall curve, Confusion matrix.
  - Training methodologies:
    - Cross Validation
    - Avoiding Overfitting

# How NLP fits in AI <a id="NLPandAI"></a>

# Modelling using RNN, LSTMs <a id ="ModellingBasic"></a>

# Advanced Modelling <a id ="Transformers"></a>


