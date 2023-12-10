# Attention mechanism

## A Textual similarity network:
1) In 1<sup>st</sup> stage, the goal is to calculate **pair-wise** word similarities.
2) Each word in sentence **a** can be similar to several words in sentence **b**, and *vice versa*.
   a) For each word w<sub>i</sub><sup>a</sup> in a sentence **a** we compute a l<sub>b</sub>-dimensional vector of its similarities to words in sentence **b**, normalized via softmax so that all similarities are positive and sum to one.
   b) This is called allignment vector for the word.
