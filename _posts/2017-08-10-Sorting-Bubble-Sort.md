---
title: "Sorting: Bubble Sort"
date: 2017-08-10
categories: 
  - Jekyll
---

Today's Cracking the Coding Interview Challenge is <a href="https://www.hackerrank.com/challenges/ctci-find-the-running-medianhttps://www.hackerrank.com/challenges/ctci-bubble-sort/problem"> 
Sorting: Bubble Sort.</a> Sorting is one of the most important topics in SE. Bubble sort is the easiest sorting algorithm in terms of 
understanding. But, since it is not an efficient algorithm it is not a widely used algorithm. The average and worst case complexity is 
O(n^2) and space complexity is O(1). Best case complexity is O(n) if the array is sorted already. 


```java
for (int i = 0; i < n; i++) {
    // Track number of elements swapped during a single array traversal
    int numberOfSwaps = 0;
    
    for (int j = 0; j < n - 1; j++) {
        // Swap adjacent elements if they are in decreasing order
        if (a[j] > a[j + 1]) {
            swap(a[j], a[j + 1]);
            numberOfSwaps++;
        }
    }
    
    // If no elements were swapped during a traversal, array is sorted
    if (numberOfSwaps == 0) {
        break;
    }
}
```

This implementation can be optimized, if we stop this process if there is no swap during one full iteration on array. 

```java
// An optimized version of Bubble Sort
void bubbleSort(int arr[], int n)
{
   int i, j;
   bool swapped;
   for (i = 0; i < n-1; i++)
   {
     swapped = false;
     for (j = 0; j < n-i-1; j++)
     {
        if (arr[j] > arr[j+1])
        {
           swap(&arr[j], &arr[j+1]);
           swapped = true;
        }
     }
 
     // IF no two elements were swapped by inner loop, then break
     if (swapped == false)
        break;
   }
}
```
