---
title: "The Must Know Topics from CTCI"
date: 2018-01-21
categories: 
  - Jekyll
---

I am reading Cracking The Coding Interview book again and there is a table that every one should know at basics. Today I am talking about them in a very basic manner.

Data Structures		        Algorithms		              Concepts

Linked Lists		           Breadth First Search		    Bit Manipulation
Binary Trees		           Depth First Search		      Singleton Design Pattern
Tries		                  Binary Search		           Factory Design Pattern
Stacks		                 Merge Sort		              Memory (Stack vs Heap)
Queues		                 Quick Sort		              Recursion
Vectors / ArrayLists		   Tree Insert / Find / etc		Big-O Time
Hash Tables				
 
Linked Lists:
Singly linkedlist implementation.

```
class Node {
    int data;
    Node next;
}
```

Doubly linked list implementation:

```
class Node {
    int data;
    Node next;
    Node prev;
}
```

Add a node to sll:
```
private void appendToTail(Node n) {
    Node node = this;
    while(node.next != null) {
        node = node.next;
    }
    node.next = n;
 }
```

Delete a node from sll:

```
private Node deleteNode(Node head, int data) {
    Node tmp = head;
    if(head == null) {
        return null;
    }
    while(head.next != null) {
        if(head.data == data) {
            head.next = head.next.next;
            return head;
        }
        tmp = tmp.next;
    }
    return head;
}
```
    
Binary Trees:

Not all binary trees are binary search trees. Why trees are used, because the data you want to store forms a tree, like filesystem.

```
class Node {
    int data;
    Node left, right;
}
```

Tree traversal's are very important and easy to understand. At top, there are two types of algorithms, depth first and breath first traversal algorithm's. As name suggest depth first algorithm's first goes to as deeper as they can, whereas breath first traversal algortihms process trees level by level. 

Depth first traversal:

Pre-order Traversal:
```java
public void preOrderTraversal(Node node) {
    if(head == null) {
        return;
     }
     //Do something, like print, count etc., this is where current node is processed
     preOrderTraversal(node.left);
     preOrderTraversal(node.right);
}
```

In-order Traversal:
```java
public void inOrderTraversal(Node node) {
    if(head == null) {
        return;
     }
     inOrderTraversal(node.left);
     //Do something, like print, count etc., this is where current node is processed
     inOrderTraversal(node.right);
}
```

Post-order Traversal:
```java
public void postOrderTraversal(Node node) {
    if(head == null) {
        return;
     }
     postOrderTraversal(node.left);
     postOrderTraversal(node.right);
     //Do something, like print, count etc., this is where current node is processed
}
```

Breadth first Traversal or Level order traversal:
```java
public void levelOrderTraversal(Node node) {
    Queue<Node> queue = new LinkedList<Node>();
    queue.add(node);
    Node tempNode;
    while(!queue.isEmpty()) {
        //Do something, like print, count etc., this is where current node is processed
        if(n.left != null)
            queue.add(n.left);
        if(n.right ! = null)
            queue.add(n.right);         
    }
}
```
