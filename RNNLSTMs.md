# RNN and LSTMs

While FeedForward netweorks can accomodate arbitrary sized sequences through the use of vector addition and concatenation [(CBOW)](NNetworks.md), such representations are quite limited and disregard the order of the features. Recurrent Neural Networks allow representing arbitrarily sized sequential inputs in a fixed-size vectors, paying attention to the structured properties of the inputs.

RNNs, particularly ones with gated architectures such as the LSTM and the GRU, are very powerful at capturing statistical regularities in sequential inputs. 

### RNNs
- One of the most promising theories was suggested by Jordan(1986).
- Jordan described a network containing recurrent connections.
- The recurrent connections allow the network's hidden units to see its own previous output, so that the subsequent behaviour can be shaped by previous responses.
- There recurrent connections are what give the Network **"Memory"**.

