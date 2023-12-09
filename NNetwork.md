#### Neural Networks
Neural networks a.k.a Deep learning is a family of learning techniques which involves learning of parameterized, differntiable mathematical functions. The name **"deep-learning"** stems from the fact that many layers of these differentiable functions are often **chained** together.
While all of machine learning can be characterized as learning to make predictions based on past observations, deep learning approaches work by learning to not only predict but also to correctly represent the data, such that it is suitable for prediction. 

- Given a large set of desired input-output mapping, deep learning approaches work by feeding the data into a network that produces successive transformations of the input data until a final transformation predicts the output. 
- The transformations produced by the network are learned from the given input-output mappings,such that each transformation makes it easier to relate the data to the desired label.

# <ins>Gradient based optimizations</ins>:
- Consider a task of finding the scalar value "x" such that the function y=f(x) is minimum at that point.
- The Canonical way is to take the 2<sup>nd</sup> order derivative of function and equate it to Zero.
- However, it is not straightforward to obtain this value for a *multiVariate* complex function, instead an **algebric** way is often employed:
  -  Take first order derivative of the function f<sup>'</sup>(x).
  -  Assume a value of 'x', x<sub>i</sub> such that u=f'(x<sub>i</sub>)
  -  If u=0, then 'x<sub>i</sub>' is the minimum value and an optimum point. So, STOP.
  -  Else, move in opposite direction of 'u' by updating:
     -    x<sub>i+1</sub> = x<sub>i</sub> - n(u), where 'n' is a *rate parameter*.
