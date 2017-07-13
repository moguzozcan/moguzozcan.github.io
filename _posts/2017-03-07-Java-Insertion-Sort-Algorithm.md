---
layout: post
title: "Insertion Sort Algorithm in Java"
date: 2017-03-07
---

Average and worst complexity is O(N^2), so this algorthm is not suitable for large data sets. In this algorithm, elements are sorted one at a time. In real world this algorithm is like sorting playing cards in our hands. 

I've solved the related hackerrank problem, see https://www.hackerrank.com/challenges/insertionsort2/problem

Assume we have an integer array named 'ar'. We sort this array by first taking the second element of the array as a key. Then we go back from the key and compare the previous elements. If the previous elements are bigger than the key, then swap the elements at location j and j+1. This process continues until we reach an element which is smaller than the key or we reach to the beginning of the array. In those cases we swap the element at j+1 with the key. printArray method is used to just print the arrays. 

```java
for (int i = 1; i < ar.length; i++) {
    int key = ar[i]; 
    int tmp;
    for (int j = i - 1; j >= 0; j--) {
        if(ar[j] > key) {
            tmp = ar[j + 1];
            ar[j+1] = ar[j];
            ar[j] = tmp;
        } else {
            ar[j+1] = key;
            break;
        }
    }
    printArray(ar);
}
```



