---
title: "Deep Learning Notes 1 Classificaiton"
date: 2018-03-28
categories: 
  - Jekyll
---

In this post, I'll share my notes in CS231N course that is thought at Stanford University. 

Image Classification is the task of assigning an input image one label from a fixed set of categories. Althought it seems
like a simple job, there are many challenges. Challenges of image recognition:

- Viewpoint variation. A single instance of an object can be oriented in many ways with respect to the camera.
- Scale variation. Visual classes often exhibit variation in their size (size in the real world, not only in terms of their extent in the image).
- Deformation. Many objects of interest are not rigid bodies and can be deformed in extreme ways.
- Occlusion. The objects of interest can be occluded. Sometimes only a small portion of an object (as little as few pixels) could be visible.
- Illumination conditions. The effects of illumination are drastic on the pixel level.
- Background clutter. The objects of interest may blend into their environment, making them hard to identify.
- Intra-class variation. The classes of interest can often be relatively broad, such as chair. There are many different types of these objects, each with their own appearance.

Image classification is one of the areas in Deep Learning at like other areas this is also a data driven approach. Since 
it is impossible to write an algorithm which detects the cats in images, we kind of need learning method. This is done by
using big data sets, actually they are called training datasets which includes images and labels of the images.

1. Collect a dataset of images and labels
2. Use Machine Learning to train a classifier
3. Evaluate the classifier on new images

The image classification pipeline:
Basically, image classification takes an image as array and assign a label to it. 

- Input: Our input consists of a set of N images, each labeled with one of K different classes. We refer to this data as the training set.
- Learning: Our task is to use the training set to learn what every one of the classes looks like. We refer to this step as training a classifier, or learning a model.
- Evaluation: In the end, we evaluate the quality of the classifier by asking it to predict labels for a new set of images that it has never seen before. We will then compare the true labels of these images to the ones predicted by the classifier. Intuitively, we’re hoping that a lot of the predictions match up with the true answers (which we call the ground truth).

Nearest Neighbor Classifier
This is one of the basic methods in image classification problems. 

We need comparing methods to compare two images for equality. One of the choice is L1 distance. For imageS I<sub>1</sub> and I<sub>2</sub> the L1 distance is defined as the following, this formula is also called as Manhattan Distance, since the streets of the Manhattan is all perpendicular to each other.

<figure>
    <a href="/assets/images/L1Distance.jpg"><img src="/assets/images/L1Distance.jpg"></a>
    <figcaption>L1 Distance equation</figcaption>
</figure>

There are many other distances in the field. Let's explain another very common one which L2 distance. It measures the euclidean distance between two vectors as follows:

<figure>
    <a href="/assets/images/L2Distance.jpg"><img src="/assets/images/L2Distance.jpg"></a>
    <figcaption>L2 Distance equation</figcaption>
</figure>

L1 vs. L2 distances:
L2 distance does not accept big difference, it rather prefers many medium sized disagreements. 

k - Nearest Neighbor Classifier


Validation sets for Hyperparameter tuning
How to select k for k-nearest neighbor classifier?
How to select which distance metric to use, L1 L2 distance?

These choices are called hyperparameters and how to select them are not obvious in many cases.

The key idea here is create a validation set among the training set and use them for a fake test to tune hyperparameters.
For instance, the CIFAR-10 data set includes 50000 training images and 10000 test images. 1000 of the training images can be used to test the trained network before doing the actual test to tune hyperparameters. 

Before that let's explain what are those sets. Mainly there are 3 types of data sets.

1. Training set: It is used to train your network.
2. Validation set: This is a small portion of your train set to tune hyperparameters before doing the actual test.
3. Test set: This is the real test data to measure the accuracy of the trained network.

If the test data is used for training the what is called overfitting occurs. If the test data is only used for testing then it is a very good resource for generalization of the classifier.  

Cross validation: If the data set in hand is small, then another tecnique is used to train the classifier. For example, the small data set is divided into 5 equal folds, this is called 5-hold cross-validation, then we use the 4 for training and use the 1 for validation. 

<figure>
    <a href="/assets/images/crossvalidation.jpeg"><img src="/assets/images/crossvalidation.jpeg"></a>
    <figcaption>Cross validation with 5 folds</figcaption>
</figure>

Pros and Cons of Nearest Neighbor classifier.
It is easy to understand and implement nearest neighbor classifier. Also, the train time is shorter. However, the drawback of it is, it takes much time to test it with real test data. In testing phase, it compares test data with every training example. In reality we want the opposite. The training time can be time consuming but the real test phase should be fast.

Computational complexity of the Nearest Neighbor classifier is an active area of research, and several Approximate Nearest Neighbor (ANN) algorithms and libraries exist that can accelerate the nearest neighbor lookup in a dataset 

References 

[1] http://cs231n.github.io/classification/