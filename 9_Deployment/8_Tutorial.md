## Boston Housing Data
For our very first time using SageMaker we will be looking at the problem of estimating the median cost of a house in the Boston area using the [Boston Housing Dataset](https://www.cs.toronto.edu/~delve/data/boston/bostonDetail.html).

We will be using this dataset often throughout this module as it provides a great example on which to try out all of SageMaker's features.

In addition, we will be using a random tree model. In particular, we will be using the [XGBoost](https://xgboost.readthedocs.io/en/latest/) algorithm. The details of XGBoost are beyond the scope of this module as we are interested in learning about SageMaker. If you would like to learn more about XGBoost I would recommend starting with the documentation which you can find at https://xgboost.readthedocs.io/en/latest/

The notebook we will be working though in this video and in the following two videos can be found in the *Tutorial* directory and is called *Boston Housing - XGBoost (Batch Transform) - High Level.ipynb*. Now that you know why **Boston Housing** and **XGBoost** are in the name, let's talk a bit about the rest of it.

First, **Batch Transform** is the method we will be using to test our model once we have trained it. This is something that we will discuss a little more later on.

Second, **High Level** describes the API we will be using to get SageMaker to perform various machine learning tasks. In particular, it refers to the Python SDK whose documentation can be found here: https://sagemaker.readthedocs.io/en/latest/. This high level approach simplifies a lot of the details when working with SageMaker and can be very useful.

#### [Training the model](https://www.youtube.com/watch?v=rqYlkCTLmIY)
##### XGBoost in Competition
There's a [list of winning XGBoost-based solutions](https://github.com/dmlc/xgboost/tree/master/demo#machine-learning-challenge-winning-solutions) to a variety of competitions, at the linked XGBoost repository.

##### Estimators
You can read [the documentation on estimators](https://sagemaker.readthedocs.io/en/latest/estimators.html) for more information about this object. Essentially, the Estimator is an object that specifies some details about how a model will be trained. It gives you the ability to create and deploy a model.

##### Training Jobs
A training job is used to train a specific estimator.

When you request a training job to be executed you need to provide a few items:

 1. A location on S3 where your training (and possibly validation) data is stored,
 2. A location on S3 where the resulting model will be stored (this data is called the model artifacts),
 3. A location of a docker container (certainly this is the case if using a built in algorithm) to be used for training
 4. A description of the compute instance that should be used.
Once you provide all of this information, SageMaker will executed the necessary instance (CPU or GPU), load up the necessary docker container and execute it, passing in the location of the training data. Then when the container has finished training the model, the model artifacts are packaged up and stored on S3.

You can see a high-level (which we've just walked through) example of training a KMeans estimator, [in this documentation](https://docs.aws.amazon.com/sagemaker/latest/dg/ex1-train-model-create-training-job.html). This high-level example defines a KMeans estimator, and uses .fit() to train that model. Later, we'll show you a low-level model, in which you have to specify many more details about the training job.

[Testing the model](https://www.youtube.com/watch?v=CZRKuS_qYtg)
##### Transformer
You can read more about the transform and wait functions, [in the transformer documentation](https://sagemaker.readthedocs.io/en/latest/transformer.html). In this case, the transformer is used to create a transform job and evaluate a trained model. The transform function takes in the location of some test data, and some information about how that test data is formatted.

Refer: Boston Housing - XGBoost (Batch Transform) - High Level.ipynb
#### References:
* [Xgboost paper](https://s3.amazonaws.com/video.udacity-data.com/topher/2018/November/5bfdf09f_xgboost/xgboost.pdf)

<br/><br/><br/>
Refer: IMDB Sentiment Analysis - XGBoost (Batch Transform).ipynb

* [Mini Project Solution](https://www.youtube.com/watch?v=utUxiW-tZrY)
* [Boston Housing In-Depth - Data Preparation](https://www.youtube.com/watch?v=TA-Ms7djeL0)
    - In the previous notebooks we looked at, we use the Python SDK to interact with SageMaker, calling this the high-level approach. Now we will look at the low level approach where we describe different tasks we want SageMaker to perform. The documentation for the low level approach can be found in the [Amazon SageMaker Developer Guide](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html)
    - Refer: Boston Housing - XGBoost (Batch Transform) - Low Level.ipynb
    - The high level approach makes developing new models very straightforward, requiring very little code. The reason this can be done is that certain decisions have been made for you. The low level approach allows you to be far more particular in how you want the various tasks executed, which is good for when you want to do something a little more complicated.
* [Boston Housing In-Depth - Creating a Training Job](https://www.youtube.com/watch?v=1CIbWNUSZXo)
* [Boston Housing In-Depth - Building a Model](https://www.youtube.com/watch?v=JJyVsmcV2M4)
* [Boston Housing In-Depth - Creating a Batch Transform Job](https://www.youtube.com/watch?v=JwPJMYRl3nw)
* Finally, we learned the basics of how models can be constructed and trained using Amazon SageMaker. In particular, we learned how Amazon S3 is used as a central storage service when using SageMaker. In order to train a model, data must first be available on S3, and once the model has been trained, the model artifacts are also stored on S3. We also saw how to use SageMaker to train models and fit them to data, saving the results (called model artifacts). Lastly, we looked at how we could use SageMaker's Batch Transform functionality to test our models.
