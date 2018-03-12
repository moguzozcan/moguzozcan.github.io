---
title: "Matrix Multiplication With MapReduce"
date: 2018-03-12
categories: 
  - Jekyll
---

MapReduce is a programming model that Google came up with to handle computation of their huge large scale data. It uses a distributed 
file system called GFS, which is Google File System. It basically consists of Master node and Chunk servers in racks. Data is kept in 
Chunk servers, the size of servers changes between 16 to 64 MB and the data is replicated for reliability. The cluster architecture is 
shown below:

<figure>
    <a href="/assets/images/gfs.jpg"><img src="/assets/images/gfs.jpg"></a>
    <figcaption>Google File System architecture</figcaption>
</figure>

Generally the number of Map functions is bigger than the size of servers and number of Reduce functions is less than number of Map functions. 

MapReduce is made of three steps. 

1. Map: Extract something that is required
2. Group by key: Sorting, shuffling etc.
3. Reduce: Aggregare, summarize, filter or transform and then give the output.

In this post, I'll explain how to accomplish a matrix multiplication task with map reduce model. 

Since matrix multiplication is done with row of the first matrix, let's call it M with size i * j, and column of the second matrix, 
call this one N with j * k, we need to make them group based on a key. This key has to be the j. 


