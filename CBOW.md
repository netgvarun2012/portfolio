# CBOW
![image](https://github.com/netgvarun2012/portfolio/assets/93938450/7c9ac59f-3297-4522-9889-7179ddfdbb94)


Feed-forward networks assume a fixed dimensional input. This can easily accommodate the case of a feature-extraction function that extracts a fixed number of features: each feature is represented as a vector, and the vectors are concatenated. This
way, each region of the resulting input vector corresponds to a different feature.

But what if the features are variable? For e.g., suppose features are words themselves such as in a document classification task.

We thus need to represent an unbounded number of features using a fixed-size vector. One way of achieving this is through a so-called continuous bag of words (CBOW ) representation.
