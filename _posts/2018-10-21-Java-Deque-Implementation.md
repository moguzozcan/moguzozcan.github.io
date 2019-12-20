---
title: "Java Deque Implementation"
date: 2018-10-21
categories: 
  - Java
  - Deque
  - Stack
  - Queue
---

The Stack and Queue classes in Java gets a little complex after they are combined in Deque interface, at least for me:) There was a Stack class used for stack related problems in Java, but now it is combined with the Deque interface implementation which is ArrayDeque.  

Firstly, deque is used for double ended queue. It is resizable and does not support concurrent access, which means it is not thread safe. [1] The important point of ArrayDeque class is that, for interview preparation, the methods of stack and queue has to be known and used accordingly. Therefore, here I will list the methods that is used for Queue and Stack implementations. 

This interface extends the Queue interface. When a deque is used as a queue, FIFO (First-In-First-Out) behavior results. Elements are added at the end of the deque and removed from the beginning. The methods inherited from the Queue interface are precisely equivalent to Deque methods as indicated in the following table:[2]

|Queue Method	              |Equivalent Deque Method
|---------------------------|-----------------------
|add(e)	                    |addLast(e)
|offer(e)	                  |offerLast(e)
|remove()	                  |removeFirst()
|poll()	                    |pollFirst()
|element()	                |getFirst()
|peek()	                    |peekFirst()


Deques can also be used as LIFO (Last-In-First-Out) stacks. **This interface should be used in preference to the legacy Stack class**. When a deque is used as a stack, elements are pushed and popped from the beginning of the deque. Stack methods are precisely equivalent to Deque methods as indicated in the table below:[2]

|Stack Method	    |Equivalent Deque Method
|-----------------|-----------------------
|push(e)	        |addFirst(e)
|pop()	          |removeFirst()
|peek()	          |peekFirst()


**References**

[1] https://www.geeksforgeeks.org/deque-interface-java-example/ 

[2] https://docs.oracle.com/javase/7/docs/api/java/util/Deque.html