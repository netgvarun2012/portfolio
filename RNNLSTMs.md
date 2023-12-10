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

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/fa58083d-0276-4ba0-abd1-29cfff838890)
