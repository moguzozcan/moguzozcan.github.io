---
layout: post
title: "Remember Heaps"
date: 2017-08-02
---

Today's Cracking the Coding Interview Challenge is <a href="https://www.hackerrank.com/challenges/ctci-find-the-running-median"> 
Heaps: Find the Running Median.</a> Heaps have always been a confusion for me. Today is the day to end this! 
<a href="https://www.youtube.com/watch?v=_D0ZQPqeJkk"> Background music:) </a>

Heaps are like special kind of trees. Heap has to follow some ordering property called heap property. There are two kind of heaps: Max Heap
and Min Heap. In max heap the value of the root node is the max among others, whereas the value of the root node is the lowest in min heap.
Also when we are talking about heaps, binary heap is intended. Binary heap is a complete binary tree, meaning of complete is, all of the 
levels of the tree are full, except the last node, which may or may not be full depending on the case. 

Heaps can easily be implemented using arrays. Since heaps are fulled from left to right, left child of node i is located at 2i + 1 and 
right child is located at 2i + 2. 
 
