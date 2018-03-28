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

The image classification pipeline:
Basically, image classification takes an image as array and assign a label to it. 

- Input: Our input consists of a set of N images, each labeled with one of K different classes. We refer to this data as the training set.
- Learning: Our task is to use the training set to learn what every one of the classes looks like. We refer to this step as training a classifier, or learning a model.
- Evaluation: In the end, we evaluate the quality of the classifier by asking it to predict labels for a new set of images that it has never seen before. We will then compare the true labels of these images to the ones predicted by the classifier. Intuitively, we’re hoping that a lot of the predictions match up with the true answers (which we call the ground truth).

Nearest Neighbor Classifier
This is one of the basic methods in image classification problems. 

We need comparing methods to compare two images for equality. One of the choice is L1 distance. For imageS I<sub>1</sub> and I<sub>2</sub> the L1 distance is defined as the following, this formula is also called as Manhattan Distance, since the streets of the Manhattan is all perpendicular to each other.

<figure>
    <a href="/assets/images/L1Distance.jpg"><img src="/assets/images/L1Distancegfs.jpg"></a>
    <figcaption>L1 Distance equation</figcaption>
</figure>

References 

[1] http://cs231n.github.io/classification/