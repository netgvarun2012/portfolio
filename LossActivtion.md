# Loss function
```
In the chain rule, the derivative of a **composite function** is equal to the product of the derivatives of inner and outer functions.
```
In context of **Deep learning**, the inner function is the **Activation function** while outer function is the **Loss/Cost function**.

In BackPropogation, you have to calculate the gradient of  the cost function which inturns calculates the gradient/derivative
Of ACTIVATION FUNCTION.

<img width="375" alt="image" src="https://github.com/netgvarun2012/portfolio/assets/93938450/be17e92a-2049-45bb-9fba-c241488c1182">

<img width="387" alt="image" src="https://github.com/netgvarun2012/portfolio/assets/93938450/a683c791-15fd-497a-a80b-d59d7e4c37a0">


## Vanishing and Exploding Gradients

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/774f381f-429f-41fa-abea-1640f9e776ad)

- **Gradients** are used to update the **weights** of the model.
- **Gradients** are calculated as the partial derivative of the **Loss Function** w.r.t the **activations**.
- If the **activations** are too large or too small, the derivative of the **Loss Funciton** will also be large or small respectively, which will cause the **Gradient** to be too large or small respectively.
- In both cases, the large or small gradients will prevent the model from converging because  the weights will not be updated enough to reach the minimum of the loss function.

![image](https://github.com/netgvarun2012/portfolio/assets/93938450/cfd205a8-64c5-4db7-8525-ad8cc9af0e1b)


![image](https://github.com/netgvarun2012/portfolio/assets/93938450/8031d4a1-d34f-485c-97eb-631e6efe845a)

Various techniques have been proposed to mitigate the vanishing gradient problem, including:
 - Different weight initialization strategies.
 - Non-Saturating activation functions (like ReLU).
 - Batch Normalization.
 - Architectures like [LSTM (Long Short-Term Memory) for recurrent neural networks](RNNLSTMs.md).

