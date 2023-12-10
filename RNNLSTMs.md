# RNN and LSTMs

While [FeedFoeward netweorks can accomodate arbitrary sized sequences through the use of vector addition and concatenation [(CBOW)](NNetworks.md), such representations are quite limited and disregard the order of the features. Recurrent Neural Networks allow representing arbitrarily sized sequential inputs in a fixed-size vectors, paying attention to the structured properties of the inputs.
RNNs, particularly ones with gated architectures such as the LSTM and the GRU, are very powerful at capturing statistical regularities in sequential inputs. 
