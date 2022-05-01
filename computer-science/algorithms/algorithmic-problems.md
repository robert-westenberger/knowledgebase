---
title: Algorithmic Problems
description: 
published: true
date: 2022-05-01T01:13:54.419Z
tags: algorithms
editor: markdown
---

# Dynamic Programming
Dynamic Programming is simplifying a complicated problem by breaking it down into simpler sub-problems in a recursive manner.
## Examples

[Coin Change Problem](/computer-science/algorithms-and-data-structures/algorithmic-problems/coin-change-problem) - Calculate how many ways you can make change for an amount of money, given a set of coins. This is a variation of the knapsack problem.


[Max Path Sum in a Pyramid of Numbers](/computer-science/algorithms-and-data-structures/algorithmic-problems/max-path-sum-in-a-pyramid-of-numbers) - Calculate the maximum sum, from the top to the bottom of a pyramid, when you're only allowed to move to adjacent numbers at each level.

[Minimum Cost Path](/computer-science/algorithms-and-data-structures/algorithmic-problems/minimum-cost-path) - Given a 2D matrix where each cell has a cost to travel, find a path from the left-top corner to the bottom-right corner with minimum travel cost. You can only move right or down. 
# Pointer Algorithms 
Algorithms that take advantage of the structure of data, using pointers, to calculate something. 
## Examples
[Detect Loop in Linked List (Floyd's Cycle Detection Algorithm](/computer-science/algorithms-and-data-structures/algorithmic-problems/detect-loop-in-linked-list) - Uses two pointers, moving through a linked list at different speeds, to detect a loop.
# Backtracking
Backtracking is a general algorithm for finding solutions to some computational problems, notably constrant satisfaction problems, that incrementally builds candidates to the solutions, and abandons a candidate ("backtracks") as soon as it determines that the candidate cannot possibly be completed to a valid solution.
## Examples
[Generate Valid Parentheses](/computer-science/algorithms-and-data-structures/algorithmic-problems/generate-valid-parentheses) - For a number `n`, generate all combinations of well-formed parentheses.

# Sliding Window Technique
A computational technique which aims to reduce the use of a nested loop and replace it with a single loop (thereby reducing time complexity).

## When to use it
For finding subarrays in an array that satisfies given conditions. 


## Examples
### Find the longest substring of a string containing distinct characters
[Longest Substring Without Repeating Characters](/computer-science/algorithms-and-data-structures/algorithmic-problems/longest-substring-without-repeating-characters)
### Find the longest substring of a string containing `k` distinct characters.
Given a string and a positive number `k`, find the longest substring of the string containing `k` distinct characters. If `k` is more than the total number of distinct characters in the string, return the whole string.
### Find all substrings of a string that are a permutation of another string.
Find all substrings of a string that contains all characters of another string. In other words, find all substrings of the first string that are anagrams of the second string.
### Find maximum length sequence of continuous ones (Using Sliding Window)
Given a binary array, find the index of 0 to be replaced with 1 to get a maximum length sequence of continuous ones.
### Count distinct absolute values in a sorted array
Given an array of sorted integers that may contain several duplicate elements, count the total number of distinct absolute values in it.