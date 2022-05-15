---
title: Maximum Subarray
description: 
published: true
date: 2022-05-15T20:24:23.166Z
tags: algorithms, dynamic-programming, arrays
editor: markdown
---

# Problem
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.


## Constraints
- 1 <= nums.length <= 10^5^
- -10^4^ <= nums[i] <= 10^4^

## Examples
**Input**: nums = [-2,1,-3,4,-1,2,1,-5,4]
**Output**: 6
**Explanation**: [4,-1,2,1] has the largest sum = 6.

**Input**: nums = [1]
**Output**: 1

**Input**: nums = [5,4,-1,7,8]
**Output**: 23

# Approach
## Divide and Conquer
We repeatedly cut the array in half, and search the halves for the max contiguous subarray sum. 

We then return the maximum of the following three: 
- Maximum subarray sum in left half (Make a recursive call)
- Maximum subarray sum in right half (Make a recursive call)
- Maximum subarray sum such that the subarray crosses the midpoint. 


## Dynamic Programming
### Kadane's Algorithm
TODO