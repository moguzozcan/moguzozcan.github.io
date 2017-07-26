---
layout: post
title: "Implementing a Queue from Two Stacks Algorithm"
date: 2017-07-26
---


Hi guys, 
In this post I will talk about the cycle detection in linked lists. I've seen this problem in the Cracking the Coding Interview 
<a href="https://www.hackerrank.com/challenges/ctci-linked-list-cycle"> Linked Lists: Detect a Cycle question.</a> At first, what 
comes to my mind is modify the node class, add a field, a boolean field whether this node is visited before. While you traverse the list
if that flag is true, bam! you have a cycle. But, this is the easy solution. In the question, Node class is not modifiable. So, I need to
do this without touching the node class. 
