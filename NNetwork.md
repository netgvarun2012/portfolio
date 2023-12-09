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


# <ins>Applying the *Gradient Descent* based optimization method to Neural Networks training:</ins>
- In order for the network to learn i.e. minimize the LOSS function, the loss function needs to be chosen cleverly so that the objective of the classification/regressions task (learning the true distribution of the data) is met.
- The function is actually a representation of a multi-layered network (along with the bias term and non-linear activations) and minimization happens as per the gradient descent algorithm:
  1. Parameter values are randomly initialized.
  2. The **Gradient** of the loss function is taken.
  3. Parameter values are plugged in (2) i.e. gradient of the loss function.
  4. Values thus obtained from (3) are subtracted from (1)
  5. Repeat.
 
  ## <ins>Perceptron Gradient Descent</ins>
  The method is based on minimizing the error between the actual and desired response at any training step.
  We want to find the augmented weight vector, **w**, that minimizes the *mean squared error (MSE)* between the desired and actual responses of the perceptron.
  The function should be differentiable and have a unique minimum such as below:
                  <img width="146" alt="image" src="https://github.com/netgvarun2012/portfolio/assets/93938450/dec6a3ce-7ee8-4aa1-a066-63d852c82741">
