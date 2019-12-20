---
title: "Matrix Multiplication With MapReduce"
date: 2018-03-12
categories: 
  - Map Reduce
  - Big Data
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

In this post, I'll explain how to accomplish a matrix multiplication task with map reduce model. There are two ways of doing this. In one Map and Reduce part, or using two Map and Reduce tasks. The latter one is like a natural join followed by grouping and aggregation. Let's first talk about the two steps calculation since this is easier one.  

Since matrix multiplication is done with row of the first matrix, let's call it M with size i * j, and column of the second matrix, 
call this one N with j * k, we need to make them group based on a key. This key has to be the j. In the map part, we need to create 
all the key value pairs for M (j, (M, i, m<sub>ij</sub>) and for N (j, (N, k, n<sub>jk</sub>). Here the M and N does not represent the whole matrix, they are the names of the matrixes. In the Reduce part, for each key value pair, take one that includes M and take another that includes N which have the same j value. Then create a new pair (i, j) as the key and the product of m<sub>ij</sub> and n<sub>jk</sub> as the value.

Now after the first step, we need to make a grouping and aggregation part. The map part here is just the identity. It basically does nothing but producing the same key value pairs for every (i, k) keys and v values. In the Reduce part, for each key (i, k) the sum of the values are calculated and assigned to this key. The result of the calculation is ((i, k), v) where v is the total sum which corresponds to the element (i, k) of the result matrix.

Matrix Multiplication with One MapReduce Step:
This is possible by doing more work in the two functions.
