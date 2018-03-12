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

![Cluster image]({{ site.url }}{{ site.baseurl }}/assets/images/gfs.jpg)

