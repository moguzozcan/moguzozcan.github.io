---
title: "Deep Learning Notes Convolutional Neural Networks"
date: 2018-04-02
categories: 
  - Jekyll
---

In this post, I'll coptinue to share my notes in CS231N course that is thought at Stanford University. 

Intermediates will be volumes, not vectors. The channels will be depths. Convolutional layer. 

Hyperparameters:
- K : Number of filters
- F : Spatial extend 
- S : Stride, how much your filter moves at a time. 
- P : Padding, ill the outside of the input. Generally zero padding is applied.

W<sub>1</sub> * H<sub>1</sub> * D<sub>1</sub>
W<sub>2</sub> * H<sub>2</sub> * D<sub>2</sub>

W<sub>2</sub> = (W<sub>1</sub> + F<sub>1</sub> + 2*P) / S + 1
H<sub>2</sub> = (H<sub>1</sub> + F<sub>1</sub> + 2*P) / S + 1
D<sub>2</sub> = K

If F = 3 -> Zero pad with 1 to preserve size spatially
If F = 5 -> Zero pad with 2
If F = 7 -> Zero pad with 3, N - F + 1

Conv -> ReLU -> Pool

Pooling layers to reduce size
Generally max pooling is used. Average pooling also exist. 

Fully Connected Layers (FC): Contains neurons that connect to the entire input volume. Takes an input volume in whatever size and outputs an N dimensional vector where N is the number of classes that the program has to choose from. 


References 

[1] https://www.youtube.com/watch?v=LxfUGhug-iQ