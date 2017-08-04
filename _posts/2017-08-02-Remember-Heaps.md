---
layout: post
title: "Remember Heaps"
date: 2017-08-02
---

Today's Cracking the Coding Interview Challenge is <a href="https://www.hackerrank.com/challenges/ctci-find-the-running-median"> 
Heaps: Find the Running Median.</a> Heaps have always been a confusion for me. Today is the day to end this! 
<a href="https://www.youtube.com/watch?v=_D0ZQPqeJkk"> Background music:) </a>

About two years ago in one of the interviews, heaps are asked to me. Although I took data structures lesson, I could not remember it. 
This is a scar in my heart :P. The reason why I could not remember heaps is I realize that I don't know why heaps are used in real life. 
For me, it is just a kind of tree with some special features. Then I searched for it, many people have the same problem that I have. 
Now;
Heaps are mainly used for priority queue implementation. Allright, what is a priority queue :)

Priority Queue:

Priority queue's are specialized version of the real queue, they store key value pairs. Instead of FIFO structure, the values are get out 
by their priorities. For example, printer example is given in [4]. If CEO a proffessor wants to print, it has more priority than a student even though the student is sent his request before. The implementation of the priority queues can be done in many ways but the most efficient way is using heaps. 

Heaps: 

Heaps are like special kind of trees. Heap has to follow some ordering property called heap properties. There are two kind of heaps: Max Heap and Min Heap. In max heap the value of the root node is the max among others, whereas the value of the root node is the lowest in min heap. Heap properties are:

1. Order property: For max heap; For every node n, the value in n is greater than or equal to the values in its children (and thus is also greater than or equal to all of the values in its subtrees). For min heap this is the opposite.

2. The SHAPE property: All leaves are either at depth d or d-1 (for some value d). All of the leaves at depth d-1 are to the right of the leaves at depth d. (a) There is at most 1 node with just 1 child. (b) That child is the left child of its parent, and (c) it is the rightmost leaf at depth d. [4]

When we are talking about heaps, mostly binary heap is intended. Binary heap is a complete binary tree, meaning of complete is, all of the levels of the tree are full, except the last node, which may or may not be full depending on the case. 

Heaps can easily be implemented using arrays. Since heaps are fulled from left to right, left child of node i is located at 2i + 1 and 
right child is located at 2i + 2. 
 
References:

[1] https://stackoverflow.com/questions/749199/when-would-i-want-to-use-a-heap
[2] https://stackoverflow.com/questions/5227976/what-is-the-use-of-the-heap-data-structure
[3] http://www.geeksforgeeks.org/priority-queue-set-1-introduction/
[4] http://pages.cs.wisc.edu/~vernon/cs367/notes/11.PRIORITY-Q.html
