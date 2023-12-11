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

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/d39f492f-50b3-43e6-92f7-4e297efc2d93)


   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/b2afbbef-bf66-46e9-a1d7-68e63305c033)

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/e2950a9a-fa32-4ff4-aadf-7228252bee6b)

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/b85aed51-4772-4d23-86f9-dbee38e0a53f)

   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/803467ba-99a7-4e40-964d-def7ad0cbb6c)

Once you have summed the **Token Embeddings** and **Positional Embeddings** , you pass the resultant vector to the **Self-Attention** layer:
  
   ![image](https://github.com/netgvarun2012/portfolio/assets/93938450/ae86fd8f-66db-4030-9772-5f69d67964f7)

The **Self-Attention** layer allows the model to analyze the relationships between inividial input tokens to better capture the CONTEXTUAL dependencies between the words:

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/84d35ad8-b426-4d32-a419-779d03ce98ce)

The  **self-attention weights** learnt during training and stored in these layers reflect the importance of each word in that input sequence to all other layers in the sequence.
   
But this does not happen once! Infact, multiple self-attention weights are learnt in parallel:

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/24cfd375-0c5d-4680-8209-5b35d3e93302)

Intuition is that different attemtion maps will learn different aspects of language in the input sequence:
   
![image](https://github.com/netgvarun2012/portfolio/assets/93938450/95a3f051-e2ad-46d1-8996-32f83f3567d2)

Now that all of the attention weights are applied to your input data, The output is passed to a fully connected FFN network , the output is a probability score for each token in your vocbulary

The data that leaves the eoncoder is a deep representation of the structure and the meaning of the sequence.

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/00c881f1-e6db-42d1-967a-c6d16e1894f9)

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/ef384447-1d7e-4928-a974-18e74bda5ef2)

This deep representation is inserted into the niddle of the Decoder to influence the decoder's self-attention mechanism.

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/4973d750-4409-4d79-bdf9-c474e54fff9d)

Then, a *start-of-sequence* special token is added to the input of the Decoder which triggers the Decoder to predict the next token which it does based on the contextual understanding that has been provided from the Encoder,

The output of the Decoder self-attention layer is passed through the Decoder's FFN and through the final SOFTMAX output layer.  At this point, we have our first token.

You continue this loop by passing the output token of the model back to the input to trigger the next token untill *end-of-sequence* token is received.

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/69728236-ca3a-4bd7-937c-c996390a8b5b)


## <ins>Illustrated Transformer</ins>:

   ![transformer_decoding_1](https://github.com/netgvarun2012/portfolio/assets/93938450/9ee74f17-3515-49d1-ad08-ed01ab88cc18)


   ![transformer_decoding_2](https://github.com/netgvarun2012/portfolio/assets/93938450/87ca8f2c-9335-452e-bd66-8e0050cb0707)





