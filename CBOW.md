# CBOW

Feed-forward networks assume a fixed dimensional input. This can easily accommodate the case of a feature-extraction function that extracts a fixed number of features: each feature is represented as a vector, and the vectors are concatenated. This
way, each region of the resulting input vector corresponds to a different feature.

But what if the features are variable? For e.g., suppose features are words themselves such as in a document classification task.

We thus need to represent an unbounded number of features using a fixed-size vector. One way of achieving this is through a so-called continuous bag of words (CBOW ) representation.

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/7c9ac59f-3297-4522-9889-7179ddfdbb94)

# This is how using CBOW, variable length inputs can be processed!

*So, the idea of CBOW is to learn word embeddings by treating them as parameters in the network.*

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
