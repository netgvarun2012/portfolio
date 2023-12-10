# Attention mechanism

## A Textual similarity network:
1) In 1<sup>st</sup> stage, the goal is to calculate **pair-wise** word similarities.
2) Each word in sentence **a** can be similar to several words in sentence **b**, and *vice versa*.
   
   i) For each word w<sub>i</sub><sup>a</sup> in sentence **a** we compute a l<sub>b</sub>-dimensional vector of its similarities to words in sentence **b**, normalized via softmax so that all similarities are positive and sum to one.

   ii) This is called allignment vector for the word.

3) We similarly compute an alignment vector for each word in **'b'**:
4) Now, for every word w<sub>i</sub><sup>a</sup> in sentence **a** we compute a vector w<sub>i</sub><sup>b</sup> by performing **weighted-sum** of the words in **b** that are aligned to w<sub>i</sub><sup>a</sup>.
5) Again, for every word w<sub>j</sub><sup>b</sup> in sentence **b** we compute a vector w<sub>j</sub><sup>a</sup> by performing **weighted-sum** of the words in **a** that are aligned to w<sub>j</sub><sup>b</sup>.

** Such weighted sum representation of a sequence of vectors, where the weights are computed by the **softmax** over scores such as described above are often referred to as **ATTENTION MECHANISM**.

<img width="955" alt="image" src="https://github.com/netgvarun2012/portfolio/assets/93938450/0534ea67-c242-4f2d-a79f-0991b34858d4">
