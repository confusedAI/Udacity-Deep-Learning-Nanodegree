* We are going to take a look at how we can improve our models using one of SageMaker's features, perform hyperparameter tuning. In many machine learning models there are some parameters that need to be specified by the model creator and which can't be determined directly from the data itself.

* Generally the approach to finding the best parameters is to train a bunch of models with different parameters and then choose the model that works best. SageMaker provides an automated way of doing this. In fact, SageMaker also does this in an intelligent way using Bayesian optimization. What we will do is specify ranges for our hyperparameters. Then, SageMaker will explore different choices within those ranges, increasing the performance of our model over time.

* In addition to learning how to use hyperparameter tuning, we will look at Amazon's CloudWatch service. For our purposes, CloudWatch provides a user interface through which we can examine various logs generated during training. This can be especially useful when diagnosing errors.

* [Introduction to Hyperparameter Tuning](https://www.youtube.com/watch?v=nah8kxqp55U) Essentially, tuning a model means training a bunch of models, each with different hyperparameters, and then choosing the best performing model. Of course, we still need to describe two different aspects of hyperparameter tuning:
    1. What is a bunch of models? In other words, how many different models should we train?
    2. Which model is the best model? In other words, what sort of metric should we use in order to distinguish how well one model performs relative to another.

* **Refer: Boston Housing - XGBoost (Hyperparameter Tuning) - High Level.ipynb**

* Generally speaking, the way to think about hyperparameter tuning inside of SageMaker is that we start with a base collection of hyperparameters which describe a default model. We then give some additional set of hyperparameters ranges. These ranges tell SageMaker which hyperparameters can be varied, with the goal being to improve the default model. <br/><br/>We then describe how to compare models, which in our instance is just by way of specifying a metric. Then we describe how many total models we want SageMaker to train.

> Note: In addition to creating a tuned model in this notebook, we also saw how the attach method can be used to create an Estimator object which is attached to an already completed training job. This method is useful in other situations as well.

* You will notice that throughout this module we train the same model multiple times. In most of the Boston Housing notebooks, for example, we train an XGBoost model with the same hyperparameters. The reason for this is so that each notebook is self contained and can be run even if you haven't run the other notebooks.

* In your case however, you've probably already created an XGBoost model on the Boston Housing training set with the standard hyperparameters. If you wanted to, you could use the attach method to avoid having to re-train the model.

#### Tuning the Sentiment Analysis Model
* **Refer: IMDB Sentiment Analysis - XGBoost (Hyperparameter Tuning).ipynb**
* [Tuning the Model](https://www.youtube.com/watch?v=Q2Vthdca49I)
* [Fixing the Error and Testing](https://www.youtube.com/watch?v=i-EjGkZ8z30)
* **Refer: Boston Housing - XGBoost (Hyperparameter Tuning) - Low Level.ipynb**
* [Creating a hyperparameter tuning job using the low level approach requires us to describe two different things](https://www.youtube.com/watch?v=vlsZ-jC5C8Y). <br/><br/>The first, is a training job that will be used as the base job for the hyperparameter tuning task. This training job description is almost exactly the same as the standard training job description except that instead of specifying HyperParameters we specify StaticHyperParameters. That is, the hyperparameters that we do not want to change in the various iterations. <br/><br/>The second thing we need to describe is the tuning job itself. This description includes the different ranges of hyperparameters that we do want SageMaker to vary, in addition to the total number of jobs we want to have created and how to determine which model is best.

* [Monitoring the Tuning Job](https://www.youtube.com/watch?v=WXjIkSHYEyM)
* [Building and Testing the Model](https://www.youtube.com/watch?v=ap7d7DZL0Ic)

<br/>

* In this lesson we took a look at how we can use SageMaker to tune a model. This can be helpful once we've found a good base model and we want to try and iterate a bit to refine our model and get a little more out of it.

* We also looked at using CloudWatch to monitor our training jobs so that we can better diagnose errors when they arise. This can be especially helpful when training more complicated models such as those in which you can incorporate your own code.
