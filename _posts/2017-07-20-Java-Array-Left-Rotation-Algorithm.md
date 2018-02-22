---
title: "Array Left Rotation Algorithm in Java"
date: 2017-07-20
categories: 
  - Jekyll
---

While I was working in Hackerrank, today I've started to solve "Cracking the Coding Interview Challenges". The first challenge is left 
rotating an array, here is the <a href="https://www.hackerrank.com/challenges/ctci-array-left-rotation"> link.</a> to that challenge.

With a little bit of mathematics, you can come up with a general formula to calculate new position of the index in the given array. 
Both algoritmic and space complexity of this algorith is O(N). We need an extra array for this and we have one for loop that move around
the array. 

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = in.nextInt();
        int k = in.nextInt();
        int a[] = new int[n];
        for(int a_i=0; a_i < n; a_i++){
            a[a_i] = in.nextInt();
        }
        
        int rotatedArr[] = new int[n];
        k = k % n; //avoid multiple rotations, make sure k is less than n
        for(int i=0; i < n; i++) {
            rotatedArr[(n - k + i) % n] = a[i];     
        }
        
        for(int i=0; i < n; i++) {
            System.out.print(rotatedArr[i] + " ");   
        }
    }
}
```

Let's analyze this a bit deeper. Say you have a memory problem and you don't want to use an extra array for this. I searched on the net
and I've found the following algorithm. Main logic is that, array is rotated one element at a time and thus you only need to store 
one element in a variable. The algorithmic complexity is O(N^2) whereas space complexity is O(1).

```java
/*Function to left rotate arr[] of size n by d*/
void leftRotate(int arr[], int d, int n) 
{
    int i;
    for (i = 0; i < d; i++)
        leftRotatebyOne(arr, n);
}

void leftRotatebyOne(int arr[], int n) 
{
    int i, temp;
    temp = arr[0];
    for (i = 0; i < n - 1; i++)
        arr[i] = arr[i + 1];
    arr[i] = temp;
}
```

Another way also exists here. Similar to the first algorithm. 
-First store the first k element into another array. 
-Shift rest of the array to the left
-Store back the k elements

```java
for(int i = 0; i < k; i++) {
    tmpArr[i] = a[i];
}

for(int i = 0; i < n - k; i++) {
    a[i] = a[i + k];
}

for(int i = 0; i < k; i++) {
    a[n - k + i] = tmpArr[i];
}        
```
Useful links:
http://www.geeksforgeeks.org/array-rotation/
