---
title: Find Permutations
description: 
published: true
date: 2022-05-13T14:51:58.682Z
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

#### Implementation (JS)
```
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
/**
 * A backtracking algorithm to list all permutations from the choices.
 * Each number choice is a unique natural number, and it is used exactly once.
 * @param {number[]} choices A choice array of unique natural numbers
 * @return {number[][]} The array containing all permutations
 */
/**
 * @param {number[]} nums
 * @return {number[][]}
 */


var permute = function (nums) {
  const answer = [];
  const backtrack = (list) => {

    if (list.length === nums.length) {
      answer.push([...list]);
      return;
    }
    for (let i = 0; i < nums.length; i++) {
      if (list.includes(nums[i])) {
        continue;
      }
      list.push(nums[i]);
      backtrack(list);
      list.splice(list.length - 1);
    }
  }
  backtrack([]);
  return answer;
};
permute([1, 2, 3]);

// answer.forEach(a=>console.log(a));
```

##### Explanation
For finding the permutations of `[1,2,3]`

First, loop through the array of numbers, 