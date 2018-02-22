---
title: "Java Cycle Detection Algorithm"
date: 2017-07-25
categories: 
  - Jekyll
---
---

Hi guys, 
In this post I will talk about the cycle detection in linked lists. I've seen this problem in the Cracking the Coding Interview 
<a href="https://www.hackerrank.com/challenges/ctci-linked-list-cycle"> Linked Lists: Detect a Cycle question.</a> At first, what 
comes to my mind is modify the node class, add a field, a boolean field whether this node is visited before. While you traverse the list
if that flag is true, bam! you have a cycle. But, this is the easy solution. In the question, Node class is not modifiable. So, I need to
do this without touching the node class. 

After some more thinking, I thought that I can store the visited nodes in a set and then check the set if a node is visited before. 
I need a unique field in objects for this. Then I encountered that, built in java data structure called HashSet. The implementation would 
be like the following:

```java
boolean hasCycle(Node head) {
    Set<Node> visited = new HashSet<>();
    while (head != null) {
        visited.add(head);
        head = head.next;
        if (visited.contains(head)) {
            return true;
        }             
    }
    return false;
}
```

A question might occur that why we did not use HashMap or HashTable. Because HashMap stores key, value pairs, while HashSet stores only 
the keys. Actually, behind the scenes HashSet is also using a HashMap. You can see the add method of the HashSet below:

```java
/**
 * @param e element to be added to this set
 * @return <tt>true</tt> if this set did not already contain the specified
 * element
 */
public boolean add(E e) {
    return map.put(e, PRESENT)==null;
}
```

Finally, this problem can be solved in a clever way. This is a very well known problem defined in the 
<a href="https://en.wikipedia.org/wiki/Cycle_detection#Tortoise_and_hare"> link.</a> We need to have two pointers to the nodes. One 
will go forward at one step while the other one will go two step at once. By this way, if there is a cycle these two will meet at some 
node. If not the faster one will end and method return false. The code is given below:

```java
boolean hasCycle(Node head) {
  if(head == null) {
      return false;
  }

  Node slow = head;
  Node fast = head.next;    
  while (slow != fast) {
      if(fast == null || fast.next == null) {
          return false;
      }        

      slow = slow.next;
      fast = fast.next.next;
  } 
  return true;
}
```
