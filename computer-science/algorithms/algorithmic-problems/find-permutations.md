---
title: Find Permutations
description: 
published: true
date: 2022-05-12T16:07:42.774Z
tags: algorithms, backtracking
editor: markdown
---

# Problem
Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

## Examples
**Input**: nums = [1,2,3]
**Output**: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

## Approach 
### Backtracking
To form a permutation, we need to 
1. Include all the elements ( this is the stopping condition / base case of the algorithm ).
2. No element can be included more than once. This means that at any state, our possible moves include only the elements we have not included before.

