# Transformers

<ins>German to English Translation using seq2seq RNN Encoder-Decoder Model</ins>

![seq2seq](https://github.com/netgvarun2012/portfolio/assets/93938450/9ec8a368-e96b-49d2-88bb-999b82f8212a)

The above seq2seq model is converting a German phrase to its English counterpart. Let’s break it down:

- Both Encoder and Decoder are RNNs.
- At every time step in the Encoder, the RNN takes a word vector (xi) from the input sequence and a hidden state (Hi) from the previous time step.
- The hidden state is updated at each time step.
- The hidden state from the last unit is known as the context vector. This contains information about the input sequence.
- This context vector is then passed to the decoder and it is then used to generate the target sequence (English phrase).
- If we use the Attention mechanism, then the weighted sum of the hidden states are passed as the context vector to the decoder.

## <ins>Challenges</ins>:
Despite being so good at what it does, there are certain limitations of seq-2-seq models with attention:

1. Dealing with long-range dependencies is still challenging.
2. The sequential nature of the model architecture prevents parallelization. These challenges are addressed by Google Brain’s Transformer concept.

## <ins>Transformer Architecture</ins>:
   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/b2afbbef-bf66-46e9-a1d7-68e63305c033)

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/e2950a9a-fa32-4ff4-aadf-7228252bee6b)

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/b85aed51-4772-4d23-86f9-dbee38e0a53f)

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/803467ba-99a7-4e40-964d-def7ad0cbb6c)

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/ae86fd8f-66db-4030-9772-5f69d67964f7)



## <ins>Illustrated Transformer</ins>:

   ![transformer_decoding_1](https://github.com/netgvarun2012/portfolio/assets/93938450/9ee74f17-3515-49d1-ad08-ed01ab88cc18)


   ![transformer_decoding_2](https://github.com/netgvarun2012/portfolio/assets/93938450/87ca8f2c-9335-452e-bd66-8e0050cb0707)





