---
title: "Java Volatile Keyword vs. Synchronized"
date: 2018-12-23
categories: 
  - Java, Volatile, Synchronized
---

This topic is greatly explained in [1], which is a very good Java blog. Here I'll try to summarize those information in my own words to remember them in the future. 

The variables in Java are stored in the **CPU cache** for the sake of speed. The variables can be reached faster while they are stored in CPU cache and not in the **main memory (RAM)**. But sometimes, if you are developing multithreaded applications, you may need to store your variables in the main memory, because each thread is running on different CPU cache, and this means that, each application will have a copy of the variable in their own CPU cache, where other threads are not able to reach. This problem is called the **Visibility Problem**. 

In these cases, defining a variable volatile makes the read and write of that variable to be made also from the main memory, not only from the CPU cache. For example, if two threads are reading a counter variable, and only one of them increases the value, in this case volatile guarantees the visibility. However, if both threads are writing to that variable, than using only volatile keyword is not enough to have both threads to see the latest value and write onto the latest value. In this cases, **synchronized** keyword must be used, to make every read and write operation becomes atomic. Instead of synchronized keyword, atomic data types like AtomicLong etc. can be used. 

Using volatile keyword of course decreases the performance of the application, because reaching main memory every time is more costly than reaching CPU cache. Thus, the keyword must be used when the visibility is really required. 

**References**

[1] http://tutorials.jenkov.com/java-concurrency/volatile.html