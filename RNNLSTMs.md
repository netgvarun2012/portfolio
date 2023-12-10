# RNN and LSTMs

While FeedForward netweorks can accomodate arbitrary sized sequences through the use of vector addition and concatenation [(CBOW)](NNetworks.md), such representations are quite limited and disregard the order of the features. Recurrent Neural Networks allow representing arbitrarily sized sequential inputs in a fixed-size vectors, paying attention to the structured properties of the inputs.

RNNs, particularly ones with gated architectures such as the LSTM and the GRU, are very powerful at capturing statistical regularities in sequential inputs. 

### RNNs
- One of the most promising theories was suggested by Jordan(1986).
- Jordan described a network containing recurrent connections.
- The recurrent connections allow the network's hidden* units to see its own previous output, so that the subsequent behaviour can be shaped by previous responses.
- There recurrent connections are what give the Network **"Memory"**.

<ins>Hidden</ins> These units are called *"hidden"* in the sense that they interact exclusively with other nodes internal to the network, and not the outside world!.

Imagine that there is a sequential input to be processed, and some clock which regulates presentation of the input to the network. Processing would then consist of the following sequence of events:
1. At time *t*, the input units receive the first input in the sequence.
2. Both the *input units* and *context units* activate the *hidden units*.
3. The *hidden units* then **feed forward** to activate the output units.
4. The  *hidden units* also **feed back** to activate the *context units*.
5. Output is compared with a teacher input, and **backpropogation** of error is used to adjust the connection stengths incrementally.
6. At time step, *t+1*, the above sequence is repeated.

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/9fb6d43d-d60c-4359-8ccd-0c8df680f993)


   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/fa58083d-0276-4ba0-abd1-29cfff838890)

      ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/dd877449-da9a-40cb-a835-46e8024a69d2)


#### <ins> RNN as a Generator</ins>
![image](https://github.com/netgvarun2012/portfolio/assets/93938450/7547919c-c829-4086-bda8-44716659035e)

#### <ins> RNN as an ENCODER-DECODER</ins>

- The **generation framework** discussed above, generates the next token based on the previously generated tokens.
- In the conditioned generation framework, the next token is generated based on the previously generated tokens, and an additional <ins>conditioning context *'c'*</ins>.

**What kind of information can be encoded in the context c?**
- Pretty much any data we can put our hands on during training, and that we find useful.
  - For example, if we have a large corpus of news items categorized into different topics, we can treat the topic as a conditioning context.
  - Our language model will then be able to generate texts conditioned on the topic.
  - If we are interested in movie reviews, we can condition the generation on the genre of the movie, the rating of the review, and perhaps the geographic region of the author.
  - We can then control these aspects when generating text.


<ins>**Another popular approach takes c to be itself a sequence, most commonly a piece of text. This gives rise to the sequence to *sequence conditioned* generation framework, also called the encoder-decoder framework**</ins>

a) The encoder summarizes the source sentence as a vector c.

b) The decoder RNN is then used to predict (using a language modeling objective) the target sequence words conditioned on the previously predicted words as well as the encoded sentence c. 

c) The encoder and decoder RNNs are trained jointly. 

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/14a74e50-354d-49a3-9a6d-43f0b8102921)

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/6869e15a-3ec8-413a-870b-b5a42ae9c000)


## <ins>Problems with RNN Encoder-Decoder Network</ins>
[https://arxiv.org/pdf/1409.1259.pdf](https://arxiv.org/pdf/1409.1259.pdf)

*The encoder extracts a **fixed-length vector representation** from a variable-length input sentence, and from this representation the decoder generates a correct, variable-length target translation.*

- At the core of all these recent works lies an encoder–decoder architecture. 
- The encoder processes a variable-length input (source sentence) and builds a fixed-length vector representation. 
- Conditioned on the encoded representation, the decoder generates a variable-length sequence (target sentence).

<img width="230" alt="image" src="https://github.com/netgvarun2012/portfolio/assets/93938450/8ae217cd-9fb5-48fe-9b00-938181e1767a">

## <ins>Solution [NEURAL MACHINE TRANSLATION BY JOINTLY LEARNING TO ALIGN AND TRANSLATE](https://arxiv.org/pdf/1409.0473.pdf)</ins> 

<img width="402" alt="image" src="https://github.com/netgvarun2012/portfolio/assets/93938450/5e56e8c1-6aca-4d66-a943-d986ab2fda74"> 


<img width="407" alt="image" src="https://github.com/netgvarun2012/portfolio/assets/93938450/338eace3-9d81-4e25-872d-af182ed18820"> 


<img width="403" alt="image" src="https://github.com/netgvarun2012/portfolio/assets/93938450/aea70b42-2b1b-4441-bfd7-1de1cc6d65e9"> 


<img width="131" alt="image" src="https://github.com/netgvarun2012/portfolio/assets/93938450/ee30f177-fc45-45d2-9221-fb38fc4bc21d"> 



### <ins>Weight Matrix</ins>

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/099016cd-edfc-49b4-9b54-a33ed58402f9)

The concept of **weight matrix sharing** in Recurrent Neural Networks (RNNs) primarily revolves around the idea of using the *same set of weights across different time steps or iterations of the network*.

In traditional feedforward neural networks, each layer has its unique set of weights connecting the neurons in one layer to the next. However, in RNNs, weight matrix sharing refers to the reusability of the same weights across multiple time steps. This sharing of weights allows the network to maintain memory and capture temporal dependencies in sequential data.

Here’s what makes a RNN recurrent: it uses the same weights for each step. More specifically, a typical vanilla RNN uses only 3 sets of weights to perform its calculations:

- W<sub>xh</sub>, used for all x<sub>t</sub> -> h<sub>t</sub> links.
- W<sub>hh</sub>, used for all h<sub>t-1</sub> -> h<sub>t</sub> links.
- W<sub>hy</sub>, used for all h<sub>t</sub> -> y<sub>t</sub> links.
   


![image](https://github.com/netgvarun2012/portfolio/assets/93938450/17fc413f-c1c6-4382-91a6-d4ea95e64b86)


![image](https://github.com/netgvarun2012/portfolio/assets/93938450/51d7eef2-8ad7-448c-b653-e4a036623f4a) 


![image](https://github.com/netgvarun2012/portfolio/assets/93938450/67da2258-c06b-48be-9b71-253cf0d04629) 


![image](https://github.com/netgvarun2012/portfolio/assets/93938450/ef856a00-b665-493f-9bb9-54d8923ce7e3) 




