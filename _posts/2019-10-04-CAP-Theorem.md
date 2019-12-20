---
title: "CAP Theorem"
date: 2019-10-04
categories: 
  - Distibuted Systems
  - CAP Theorem
---

Lately, I came accross with the CAP Theorem a few times so I want to read and learn about it. CAP states for Consistency, Availability, and Partition Tolerance and this theorem states that in a distributed system, these three cannot exist in the same time. At least one of them has to be sacrificied to have the others. Let's explain them one by one to understand the reasoning. The [2] is one of the best resource that explains this in plain English. 

**Consistency**

In a DS, an update is made in one of the nodes of the system and then a get request is made and if this get request is directed to another node in the system, the request should return the latest information and all of the nodes should be aware of the latest updates and they all should return the same response.

**Availability** 

The system should return to any call without any errors.

**Partition Tolerance**

Partition means something that is divided or separate or divide something. If the connection between the node is lost, the system should work without affecting. In this case partition means if the true data is divided between nodes, they should return the correct information.

<figure>
    <a href="/assets/images/cap_theorem.jpeg"><img src="/assets/images/cap_theorem.jpeg"></a>
    <figcaption>VENN Diagram of the CAP Theorem</figcaption>
</figure>

**Wikipedia explanation**

CAP theorem is found by computer scientist Eric Brewer at 2000 and theorem is also named Brewer's theorem after. Theorem states that it is impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees:

**Consistency:** Every read receives the most recent write or an error

**Availability:** Every request receives a response that is not an error

**Partition tolerance:** The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes

In particular, the CAP theorem implies that in the presence of a network partition, one has to choose between consistency and availability. Note that consistency as defined in the CAP theorem is quite different from the consistency guaranteed in ACID database transactions. [3]


**Run Around Clerk** 

Clerk means writer, recorder or office worker. Eventual consistency can be provided with a run around clerk. This is a backgroud task that works to update the nodes without affecting their work and provides synchronization of the all nodes. Many NoSQL systems are working like that. However, for a small period of time consistency may not be provided. But, if there is too less time between an update and a select or get request. 

**References**

[1] https://www.interviewbit.com/tutorial/cap-theorem/#cap-theorem

[2] http://ksat.me/a-plain-english-introduction-to-cap-theorem/

[3] https://en.wikipedia.org/wiki/CAP_theorem



<div id="brinza-task-description">
<p>In this problem we consider binary trees, represented by pointer data structures.</p>
<p>A <i>binary tree</i> is either an empty tree or a node (called the <i>root</i>) consisting of a single integer value and two further binary trees, called the <i>left subtree</i> and the <i>right subtree</i>. For example, the figure below shows a binary tree consisting of six nodes. Its root contains the value 5, and the roots of its left and right subtrees have the values 3 and 10, respectively. The right subtree of the node containing the value 10, as well as the left and right subtrees of the nodes containing the values 1, 20 and 21, are empty trees.</p>
<p><img class="inline-description-image" src="https://codility-frontend-prod.s3.amazonaws.com/media/task_static/tree_visibility/static/images/auto/c5be6ab2a497c94c69b802d7858c49aa.png"></p>
<p>A binary tree can be given using a pointer data structure. Assume that the following declarations are given:</p>
<blockquote><p style="font-family: monospace; font-size: 9pt; display: block; white-space: pre-wrap"><tt>class Tree {
  public int x;
  public Tree l;
  public Tree r;
}</tt></p></blockquote>
<p>An empty tree is represented by an empty pointer (denoted by <tt style="white-space:pre-wrap">null</tt>). A non-empty tree is represented by a pointer to an object representing its root. The attribute <tt style="white-space:pre-wrap">x</tt> holds the integer contained in the root, whereas attributes <tt style="white-space:pre-wrap">l</tt> and <tt style="white-space:pre-wrap">r</tt> hold the left and right subtrees of the binary tree, respectively.</p>
<p>A <i>path</i> in a binary tree is a non-empty sequence of nodes that one can traverse by following the pointers. The <i>length</i> of a path is the number of pointers it traverses. More formally, a path of length K is a sequence of nodes P[0], P[1], ..., P[K], such that node P[I + 1] is the root of the left or right subtree of P[I], for 0 ≤ I &lt; K. For example, the sequence of nodes with values 5, 3, 21 is a path of length 2 in the tree from the above figure. The sequence of nodes with values 10, 1 is a path of length 1. The sequence of nodes with values 20, 3, 21 is not a valid path.</p>
<p>The <i>height</i> of a binary tree is defined as the length of the longest possible path in the tree. In particular, a tree consisting of only one node has height 0 and, conventionally, an empty tree has height −1. For example, the tree shown in the above figure is of height 2.</p>
<p>A binary tree T is given. A node of tree T containing value V is described as <i>visible</i> if the path from the root of the tree to that node does not contain a node with any value exceeding V. In particular, the root is always visible and nodes with values lower than that of the root are never visible.</p>
<p>For example, the tree shown in the above figure has four visible nodes: namely, those with values 5, 10, 20 and 21. The node with value 1 is not visible because there is a node with value 10 on the path from the root to that node. The node with value 3 is not visible because its value is lower than that of the root, which has value 5.</p>
<p>Write a function:</p>
<blockquote><p style="font-family: monospace; font-size: 9pt; display: block; white-space: pre-wrap"><tt>class Solution { public int solution(Tree T); }</tt></p></blockquote>
<p>that, given a binary tree T consisting of N nodes, returns its number of visible nodes. For example, given the tree shown in the figure above, the function should return 4, as explained above.</p>
<p>Given tree T with the following structure:</p>
<p><img class="inline-description-image" src="https://codility-frontend-prod.s3.amazonaws.com/media/task_static/tree_visibility/static/images/auto/a363d9d7c2f16430a2dfcc0bd1d80b95.png"></p>
<p>the function should return 2, because the only visible nodes are those with value 8.</p>
<p>For the purpose of entering your own test cases, you can denote a tree recursively in the following way. An empty binary tree is denoted by <tt style="white-space:pre-wrap">None</tt>. A non-empty tree is denoted as (X, L, R), where X is the value contained in the root and L and R denote the left and right subtrees, respectively. The trees from the above two figures can be denoted as:</p>
<tt style="white-space:pre-wrap">  (5, (3, (20, None, None), (21, None, None)), (10, (1, None, None), None))</tt>
<p>and:</p>
<tt style="white-space:pre-wrap">  (8, (2, (8, None, None), (7, None, None)), (6, None, None))</tt>
<p>Write an <b><b>efficient</b></b> algorithm for the following assumptions:</p>
<blockquote><ul style="margin: 10px;padding: 0px;"><li>N is an integer within the range [<span class="number">0</span>..<span class="number">50,000</span>];</li>
<li>each value in tree T is an integer within the range [<span class="number">−100,000</span>..<span class="number">100,000</span>];</li>
<li>the height of tree T (number of edges on the longest path from root to leaf) is within the range [<span class="number">−1</span>..<span class="number">500</span>].</li>
</ul>
</blockquote></div>