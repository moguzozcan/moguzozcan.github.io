---
title: "Implementing a Queue from Two Stacks Algorithm"
date: 2017-07-26
categories: 
  - Jekyll
---

Hi guys, 
In this post I will talk about the implementing a queue data sturcture from existing data structures called stacks and I need to use two
of them. I've seen this problem in the Cracking the Coding Interview  
<a href="https://www.hackerrank.com/challenges/ctci-queue-using-two-stacks"> Queues: A Tale of Two Stacks.</a> 

Actually, stack data structure in Java is not recommended to use anymore. Instead, ArrayDeque is recommended, which implements Deque 
interface. Here is the javadoc notes: "This class is likely to be faster than Stack when used as a stack, and faster than LinkedList when used as a queue." 

Since this question is old, I've preferred to use stacks. Now, the question is given in the above link. We need to implement a queue 
from two stacks. The first idea that comes to mind is: 
1. Queue push(): push all data from one stack to another, add the new element at the bottom of the empty stack, and fill the stack again.
2. Queue pop(): push all data from one stack to another, pop the element from the new stack, and put all elements back.
3. Queue peek(): push all data from one stack to another, poeek the element from the new stack, and put all elements back.

Although the logic works, this is not the optimal solution. For all operations, we are carrying a whole stack into another and put back. 
So, we need a better solution! 

Question is: Do we really need to carry all the data at all times? Or is it okey to carry when the second stack is empty?

Answer: At first, we have two stacks, one is for enqueue and other one is for dequeue stack. We are pushing all the elements into
stack s2 if it is empty. If it is not, the order of the elements are preserved, so no need to do anything. Here is the sample code:

```java
static class MyQueue<T>{
  Stack<T> s1;
  Stack<T> s2;
  MyQueue(){
      s1 = new Stack<T>();
      s2 = new Stack<T>();
  }

  protected void enqueue(T t) {
      s1.push(t);
  }

  protected void dequeue() {
      if(s2.isEmpty()){
          while(!s1.isEmpty()){           
             s2.push(s1.pop());
          }
      }
      s2.pop();
  }

  protected String peek() {
      if(s2.isEmpty()){
          while(!s1.isEmpty()){           
             s2.push(s1.pop());
          }
      }
      return s2.peek().toString();
  }
}
```
