## Pytorch -- Deep learning framework
 * PyTorch was released in early 2017 and has been making a pretty big impact in the deep learning community. It's developed as an open source project by the Facebook AI Research team, but is being adopted by teams everywhere in industry and academia.

 * We'll cover tensors - the main data structure of PyTorch. Then we'll learn about a module called autograd that PyTorch uses to calculate gradients for training neural networks. Autograd does all the work of backpropagation for us by calculating the gradients at each operation in the network which we can then use to update the network weights.

#### Dependencies
 * The notebooks provided require PyTorch v0.4 or newer, and torchvision. The easiest way to install PyTorch and torchvision locally is by following [the instructions on the PyTorch site](https://pytorch.org/get-started/locally/). Choose the stable version, your appropriate OS and Python versions, and how you'd like to install it. You'll also need to install numpy and jupyter notebooks, the newest versions of these should work fine. Using the conda package manager is generally best for this:<br/>
     ***conda install numpy jupyter notebook***

 * The final part of the series has a soft requirement of a GPU used to accelerate network computations. Even if you don't have a GPU available, you'll still be able to run the code and finish the exercises. PyTorch uses a library called [CUDA](https://developer.nvidia.com/cuda-zone) to accelerate operations using the GPU. If you have a GPU that CUDA supports, you'll be able to install all the necessary libraries by installing PyTorch with conda. If you can't use a local GPU, you can use cloud platforms such as [AWS](https://docs.aws.amazon.com/dlami/latest/devguide/gpu.html), [GCP](https://cloud.google.com/gpu/), and [FloydHub](https://www.floydhub.com/) to train your networks on a GPU.

### Part 1 - Tensors in PyTorch.ipynb
 * Tensors are the base data structures that we use in neural network frameworks. Tensor is the generalization of vectors and matrices. Tensor with zero dimension is scalar, with one dimension is vector, with two dimension is matrix and so on. Tensorflow is named after tensors. Numpy arrays, after all, are just tensors.  Commands :<br/>
**import torch** -- imports pytorch<br/>
**torch.randn((1,5))** -- randn creates a tensor of five samples from 5 different normal random variables individually.<br/>
**torch.randn(5)** -- here, randn creates a tensor of five samples from one normal random variable.<br/>

### Part 2 - Neural Networks in PyTorch
 * Pytorch has a module *nn* that has lot of classes, methods and functions that allow us to build large neural networks in very efficient way.

 * We'll see torchvision package that sits alongside PyTorch and provides a lot of utilities like datasets, models for computer vision problems.

 * [Building NN with Pytorch](https://www.youtube.com/watch?time_continue=421&v=8KRX7HvqfP0)
 *

### Part 3 - Training Neural Networks in Pytorch
 * We're using the example of Handwritten Digit Recognition in this part.<br/> Training means we're going to use our neural network with non-linear activations as a [universal function approximator](http://neuralnetworksanddeeplearning.com/chap4.html). What that means is that, if we have the correct dataset of the images that are labeled with the correct digits, then eventually our neural network will build to approximate the function that converts the images into the probability distribution with a lot of probability on the correct digit in the image. Basically we'll now see in PyTorch, how we adjust the weights and biases of the network so that it approximates the function.

 * We'll need what is called a loss function, a measure of our prediction error i.e. how far away our networks prediction is from the correct label. Then the whole goal is to adjust our network parameters to minimize loss, and this is done using gradient descent. Gradient is the slope of the loss function with respect to parameters. The gradient always points in the direction of fastest change, to increase loss and we want to get to the minimum of our loss, so we just go in the opposite direction of gradient. With multilayered neural networks, we use an algorithm called backpropagation(a faster way to apply multivariable chain rule) to calculate
 gradient.

 * PyTorch has a module called Autograd that automatically calculates the gradients of our tensors. The way it works is that,PyTorch will keep track of all the operations we do on a tensor and when we want it to do a backwards pass,
 through each of those operations and calculate the gradients with respect to the input parameters it will do it. [Autograd](https://www.youtube.com/watch?v=zBWlOeX2sQM)

### Part 5 - Inference and Validation


[Part 6 - Saving and Loading Models](https://www.youtube.com/watch?v=3ZJfo2bR-uw)<br/>
[Part 7 - Loading Image Data](https://www.youtube.com/watch?v=hFu7GTfRWks)

### Part 8 - Transfer Learning
At last we'll see a pre-trained network which solves the problem of classifying cat and dog images. The network was trained on ImageNet, a massive dataset of over one million labeled images from 1,000 different categories. Using torchvision.models module we can download our pre-trained network.<br/>
Transfer learning focuses on storing knowledge gained while solving one problem and applying it to a different but related problem. For example, knowledge gained while learning to recognize cars could apply when trying to recognize trucks. Here we'll use transfer learning (what's learned from ImageNet dataset is being transferred to our dataset) to train a network which can be used to classify cats and dogs.
