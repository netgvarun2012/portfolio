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
  
![image](https://github.com/netgvarun2012/portfolio/assets/93938450/42801c45-bc3d-42d6-b72c-93d1470d3b1d)

- Each core feature is embedded into a ‘d’ dimensional space and represented as a vector in that space.
- The dimension ‘d’ is usually much smaller than the number of features, i.e., each item in a vocabulary of 40,000 items (encoded as 40,000-dimensional one-hot vectors) can be represented as a 100 or 200-dimensional vector.
- The embeddings (the vector representation of each core feature) are treated as parameters of the network and are trained like the other parameters of the function f.
  
  ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/b6c81d6a-d33c-44d5-8c25-7d6fd0ce604c)

# AI Basics <a id="AIBasics"></a>

The above diagram captures the main steps and the flow of the process:

