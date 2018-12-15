## Sigmoid Neuron
**Why move from Perceptron to Sigmoid neuron ?**
<br/>--- I don't understand the reason precisely for now. But let's discuss Sigmoid Neuron.

 * Sigmoid Neuron is like a perceptron, except the inputs $x_1,x_2,…$ instead of being just 0 or 1, can also take on any values between 0 and 1. So, for instance, 0.638… is a valid input for a sigmoid neuron, and similarly the output is not just 0 or 1. Instead, it's $σ(w⋅x+b)$, where σ is called the sigmoid function, and is defined by:
                 $σ(z)=\frac{1}{1+e^{−z}}$
 <br/>σ is sometimes called the logistic function, and this new class of neurons called logistic neurons. It's useful to remember this terminology, since these terms are used by many people working with neural nets. However, we'll stick with the sigmoid terminology.

 * To put it all a little more explicitly, the output of a sigmoid neuron with inputs $x_1,x_2,…,$ weights $w_{1},w_{2},…,$ and bias b is:=$\frac{1}{1+e^{(−\sum_{j}w_jx_j−b)}}$

#### The Softmax Function
The softmax function is equivalent of the sigmoid activation function, but when the problem has 3 or more classes. Let's say we have N classes

**Softmax for n=2 classes is same as the sigmoid function**
