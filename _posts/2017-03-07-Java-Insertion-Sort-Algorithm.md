---
title: "Insertion Sort Algorithm in Java"
date: 2017-03-07
categories: 
  - Jekyll
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

This code can also be written with a while loop.

```java
public static void insertionSort(int[] A){
    for(int i = 1; i < A.length; i++){
        int value = A[i];
        int j = i - 1;
        while(j >= 0 && A[j] > value){
            A[j + 1] = A[j];
            j = j - 1;
        }
        A[j + 1] = value;
    }

    printArray(A);
}
 ```

Helpful links:
https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif
http://www.geeksforgeeks.org/insertion-sort/
https://www.tutorialspoint.com/data_structures_algorithms/insertion_sort_algorithm.htm
http://www.studytonight.com/data-structures/insertion-sorting
