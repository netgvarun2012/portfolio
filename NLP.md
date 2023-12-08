NLP is a specialized area in AI that exclusively deals with processing of Natural language including understanding, generating text such as individual characters, words, paragraphs, documents such as whole of Wikipedia. 

# Table of Contents
  * [Basic NLP concepts](#concepts)
  * [AI Basics](#AIBasics)
  * [How NLP fits in AI](#NLPandAI) 
  * [Modelling using RNN, LSTMs](#ModellingBasic)
  * [Advanced Modelling (Transformers)](#ModellingAdvances)
  * [Generative AI](#GENAI)


# Basic NLP Concepts <a id="concepts"></a>

Language is **symbolic and discrete**. Both characters and words are discrete symbols. The basic elements of written langugage are characters. Characters form words that in turn denote objects, concepts, events, actions, and ideas. For instance, words such as "hamburger" or "pizza" each evoke in us a certain mental representations, but they are also distinct symbols, *whose meaning is external to them and left to be interpreted in our heads.*

While in Computer Vision (CV) or Speech Processing, basic building blocks are continuous in nature, allowing, for exanple, to move from a colorful image  to a gray-scale one using a simple mathematical operation, or to compare two different colors based on their inherent properties such as hue and intensity. This can not be done easily with words - *there is no simple operation that will allow us to move from the word "red" to the word "pink" without using a large lookup table or dictionary*.

Language is also compositional: letters form words, and words form phrases and sentences. In order to interpret a text, we thus need to work beyond the level of letters and words, and look at long sequences of words such as sentences, or even complete documents.

The combination of the above properties leads to data sparseness. e way in which words (discrete symbols) can be combined to form meanings is practically infinite. e number of possible valid sentences is tremendous: we could never hope to enumerate all of them. 

#### Challenges for computational approaches when dealing with NLP:
  1. Language is discrete.
  2. Language is sparse.
  3. Language is compositional.
  4. Language is ambiguous and often consists of variable number of inputs.

# *Converting discrete words into continuous numeric representation*

#### Solution - [Neural Networks](NNetwork.md) with an Embedding layer: 

- Major component in neural networks for language is the use of an embedding layer, a mapping of discrete symbols to continuous vectors in a relatively low dimensional space.
- When embedding words, they transform from being isolated distinct symbols into mathematical objects that can be operated on. This capability alleviates to some extent the **discreteness and data-sparsity** problems.

# AI Basics <a id="AIBasics"></a>

The above diagram captures the main steps and the flow of the process:

