### Perceptron -- For linearly separable data

 * The most fundamental unit of a deep neural network is called an artificial neuron which takes an input, processes it, passes it through an activation function like the Sigmoid, return the activated output. There are various types of artificial neuron: perceptron,sigmoid neuron,etc. **In this post, we are only going to talk about the _perceptron model_ proposed before the _activation neurons_ came into the picture.**

 * The perceptron model, proposed by Minsky-Papert, is a more general computational model than [McCulloch-Pitts neuron](https://towardsdatascience.com/mcculloch-pitts-model-5fdf65ac5dd1). Inputs can take only boolean values.
 ![alt text](Images/per.png) This is very similar to an Mc-Pi neuron except we take a weighted sum of the inputs and set the output as one only when the sum is more than an arbitrary threshold, $\theta$. By varying the weights and the threshold, we can get different models of decision-making.

 * However, according to the convention, instead of hand coding the thresholding parameter $\theta$, we add it as one of the inputs, with the weight -$\theta$ like shown below, which makes it learnable.![alt text](Images/per1.png) w_0 is called the perceptron's bias. Think of the bias as a measure of how easy it is to get the perceptron to output a 1. Or to put it in more biological terms, the bias is a measure of how easy it is to get the perceptron to fire. For a perceptron with a really big bias, it's extremely easy for the perceptron to output a 1. But if the bias is very negative, then it's difficult for the perceptron to output a 1.

 * It's obvious from the above figure a perceptron separates the input space into two halves, positive and negative. All the inputs that produce an output 1 lie on one side (positive half space) and all the inputs that produce an output 0 lie on the other side (negative half space). **So, a single perceptron can only be used to implement linearly separable functions.**

 * **The perceptron algorithm is an learning algorithm for supervised learning of binary classifiers. Perceptron is a type of linear classifier, i.e. a classification algorithm that makes all of its predictions based on a linear predictor function combining a set of weights with the feature vector.**<br>
 The job of a perceptron is to learn linear decision boundary (n-1 dimensional hyperplane) i.e. it has to learn a model, given by $w_{1}x_{1} + w_{2}x_{2}+...+ w_{n}x_{n} + b$, so that $\hat{y}$(our predicion) resembles y(actual labels) as close as possible on training data.**Again mind you that Perceptron is not a Sigmoid neuron and we’re not going to do any Gradient Descent.**

 * Perceptrons as Logical Operators ![alt text](Images/And.png "And Perceptron") ![alt text](Images/Or.png "Or Perceptron") **A single perceptron cannot learn to separate the data that are non-linear in nature. But we can use networks of perceptrons to compute any logical function.** ![alt text](Images/XOR.png "XOR Perceptron")

 * Perceptron Learning Algorithm ![alt text](Images/Algo.png "Perceptron Algorithm") We just repeat the above algorithm until the number of errors is small or we could run the algorithm just say, 1000 times(epochs) and stop.



References:
 * [Introduction to Perceptron](https://towardsdatascience.com/perceptron-the-artificial-neuron-4d8c70d5cc8d)
 * [Perceptron Learning Algorithm](https://towardsdatascience.com/perceptron-learning-algorithm-d5db0deab975)
 * [Detailed nice post](http://neuralnetworksanddeeplearning.com/chap1.html)
