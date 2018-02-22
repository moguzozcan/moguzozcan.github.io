---
title: "Next Permutation Algorithm in Java"
date: 2017-02-27
categories: 
  - Jekyll
---

In this post, I will tell you how to write the next permutation algorithm in Java. I've encountered this problem in one of the hackerrank 
<a href=" https://www.hackerrank.com/challenges/bigger-is-greater">challenge.</a>. Java is missing built-in nextPermutation() method,
whereas C++ has <a href="http://www.cplusplus.com/reference/algorithm/next_permutation/">one.</a> So, we need to build our own method.
This method can be used to sort data lexicographically. 

There is a wikipedia <a href="https://en.wikipedia.org/wiki/Permutation#Generation_in_lexicographic_order">link</a> I suggest you to read to better understand the topic. Now this algorithm is not as complex as it seems. Moreover, this guy also explained very well
<a href="https://www.nayuki.io/page/next-lexicographical-permutation-algorithm"> in his blog.</a>The logic behind this is: 

 -Sort the sequence in increasing order
 -Repeat the following algorithm until it returns false:
    Find the largest index k such that a[k] < a[k + 1]. If no such index exists, the permutation is the last permutation.
    Find the largest index l greater than k such that a[k] < a[l].
    Swap the value of a[k] with that of a[l].
    Reverse the sequence from a[k + 1] up to and including the final element a[n].

So, an example code piece is like the following:

```java
public void nextPermutation(int[] nums) {
    if(nums == null || nums.length<2)
        return;
 
    int p=0;            
    for(int i=nums.length-2; i>=0; i--){
        if(nums[i]<nums[i+1]){
            p=i;
            break;
        }    
    }
 
    int q = 0;
    for(int i=nums.length-1; i>p; i--){
        if(nums[i]> nums[p]){
            q=i;
            break;
        }    
    }
 
    if(p==0 && q==0){
        reverse(nums, 0, nums.length-1);
        return;
    }
 
    int temp=nums[p];
    nums[p]=nums[q];
    nums[q]=temp;
 
    if(p<nums.length-1){
        reverse(nums, p+1, nums.length-1);
    }
}
 
public void reverse(int[] nums, int left, int right){
    while(left<right){
        int temp = nums[left];
        nums[left]=nums[right];
        nums[right]=temp;
        left++;
        right--;
    }
}
```
