---
layout: post
title: "Review Binary Trees and Binary Search Trees"
date: 2017-07-26
---

Hi guys, 
In this post I will review the BT and BST topics. I've seen this problem in the Cracking the Coding Interview  
<a href="https://www.hackerrank.com/challenges/ctci-is-binary-search-tree"> Trees: Is This a Binary Search Tree?</a> link. 

Now, binary tree is a tree data structure, where each node might have at most two child nodes called left and right. Height of the tree
is calculated recursively as: height(t) = 1 + max(height(root.left), height(root.right))

Whereas, a binary search tree is a special kind of binary tree, where all the nodes in left of a node is <= ancestor and all the nodes
in the right of a node is > value of the node itself. Advantage of the BST is that, since it has a special way of storing elements, sorting
is very fast. You only need to compare two child nodes and according to result you eliminate half of the tree. Inserting or searching 
a balanced bst is O(log(n)). Whereas, the bst can easily became unbalanced according to the insertion order. This makes inserting and 
sorting complexity to O(n).

Another important topic in trees is tree traversal. There are four types of traversing the trees:

1. InOrder Traversal:
left-root-right order

2. PostOrder Traversal:
left-right-root order

3. PreOrder Traversal: as deeply to the left as possible, it's also known as a depth-first-search or DFS
root-left-right order

4. Level Order Traversal: A level-order traversal of tree  is an algorithm that processes the root, followed by the children of the 
root (from left to right), followed by the grandchildren of the root (from left to right)
 breadth-first-search (BFS)
 
      4
  2       6
1   3   5   7  
The binary tree above has the following traversals:

InOrder: 1 2 3 4 5 6 7
PostOrder: 1 3 2 5 7 6 4
PreOrder: 4 2 1 3 6 5 7
Level-Order: 4 2 6 1 3 5 7

```java

