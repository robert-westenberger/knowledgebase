---
title: WORK IN PROGRESS: Get Count Of Smaller Numbers After Particular Number In An Array
description: 
published: true
date: 2022-04-28T16:47:59.620Z
tags: algorithms
editor: markdown
---

# Problem
(From https://leetcode.com/problems/count-of-smaller-numbers-after-self/)
You are given an integer array nums and you have to return a new counts array. The counts array has the property where counts[i] is the number of smaller elements to the right of nums[i].

Input: nums = [5,2,6,1]
Output: [2,1,1,0]
Explanation:
To the right of 5 there are 2 smaller elements (2 and 1).
To the right of 2 there is only 1 smaller element (1).
To the right of 6 there is 1 smaller element (1).
To the right of 1 there is 0 smaller element.

# Algorithm using mergesort

