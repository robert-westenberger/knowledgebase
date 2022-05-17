---
title: Squares of a Sorted Array
description: 
published: true
date: 2022-05-17T16:59:14.703Z
tags: algorithms, two-pointers
editor: markdown
---

# Problem
Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

 
## Constraints
- 1 <= nums.length <= 10^4^
- -10^4^ <= nums[i] <= 10^4^
- nums is sorted in non-decreasing order.

## Examples
Example 1:

**Input**: nums = [-4,-1,0,3,10]
**Output**: [0,1,9,16,100]
**Explanation**: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].

Example 2:

**Input**: nums = [-7,-3,2,3,11]
**Output**: [4,9,9,49,121]
 


# Approach
We use two pointer technique to square and sort the list in `O(n)` time. Taking note of how the numbers on either side of the unsquared list will be the largest values in the squared list, we can start with pointers on both the left and right ends of the list and converge towards the middle. 

## Implementation (Javascript)
```
const sortedSquares = function(nums) {
    let left = 0;
    let right = nums.length - 1;
    const answer = [];
    while (left <= right) {
        const num1 = Math.pow(nums[left], 2);
        const num2 = Math.pow(nums[right], 2);
        if (left === right) {
            answer.unshift(num1);
            break;
        }
        else if (num1 > num2) {
            answer.unshift(num1);
            left++; 
        } else {
            answer.unshift(num2);  
            right--; 
        }
    }
    return answer;
};
```