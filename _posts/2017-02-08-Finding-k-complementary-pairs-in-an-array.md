---
title: "Finding K-complementary pairs in an integer array, Java"
date: 2017-02-08
categories: 
  - Jekyll
---

Hi,
This is the second post today, it is again related with the interview question that I've received. The question is "Write an 
efficient algorithm to find K-complementary pairs in a given array of integers, pair (i, j) is K-complementary if 
K = A[i] + A[j];"

The first algorithm that comes to mind is having two nested for loops and sum the pairs, if they equal K, than you are done, 
like this:

```java
public int complementaryPairs(int arr[],int k) { 
	for(int i = 0; i <= arr.length; i++) {
		for(int j = i; j < arr.length-1; j++) {
			if(arr[i] + arr[j+1] == k) {
			   System.out.println(i + " " + j);
			}
		}
	}
}
```
The time complexity of this algorithm is O(N^2), n square, and space complexity is O(1). Actually, I am not sure whether I 
have to store the pairs in a collection or not, if I have, then space complexity will increase. 



