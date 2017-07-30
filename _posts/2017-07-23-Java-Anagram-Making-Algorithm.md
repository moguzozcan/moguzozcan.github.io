---
layout: post
title: "Java HashMap vs. HashTable"
date: 2017-07-23
---

When I was solving the third challenge in Cracking the Coding Interview tasks in hackerrank, I've come accross with HashTables. Then I 
realized that I forget the difference between HashMap and HashTable in Java. So, in this post firstly I'll explain their differences
and then I will put my solution to the 3rd challenge. 

Both of mainly does the same job at the end. There is a hidden hash function in behind. When you put somethind inside the container, 
memory location is calculated according to that. When you pull or get something from it, you can reach that element in O(1). Hash function
is used when putting and pulling the element from the container. 

1. HashTable is a sychronized container, whereas HashMap is not. Therefore, HashMap is faster than HashTable but it is not suitable for 
multithread applications. 

2. Putting null objects into HashTable is not possible, but HashMap accepts null key and values. 

Now, the question int the hackerrank is given in the <a href="https://www.hackerrank.com/challenges/ctci-ransom-note"> Hash Tables: Ransom 
Note</a> link. 


 
