---
title: "Deep Learning Notes 2 Linear Classificaiton"
date: 2018-03-29
categories: 
  - Jekyll
---

In this post, I'll coptinue to share my notes in CS231N course that is thought at Stanford University. 

Since kNN is not a good choice for image classification a more powerful method is developed. In this method there are two main components. 

**Score function:** Maps the raw data to class scores
**Loss function:** Quantifies the agreement between the predicted scores and the ground truth labels.

Main idea is optimize the problem by minimizing the loss function wrt parameters of the score function.

**Linear classifier**


<figure>
    <a href="/assets/images/linearclassifier.jpeg"><img src="/assets/images/linearclassifier.jpeg"></a>
    <figcaption>Linear classification</figcaption>
</figure>



References 

[1] http://cs231n.github.io/linear-classify/