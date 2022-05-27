---
title: 0 1 Matrix
description: Given an m x n binary matrix mat, return the distance of the nearest 0 for each cell.
published: true
date: 2022-05-27T17:58:44.720Z
tags: matrix, algorithms, breadth-first-search
editor: markdown
---

# Problem
Given an m x n binary matrix mat, return the distance of the nearest 0 for each cell.

The distance between two adjacent cells is 1.

## Examples
Input: mat = [
[0,0,0],
[0,1,0],
[0,0,0]
]
Output: [
[0,0,0],
[0,1,0],
[0,0,0]
]

Input: mat = [
[0,0,0],
[0,1,0],
[1,1,1]
]
Output: [
[0,0,0],
[0,1,0],
[1,2,1]
]
## Constraints
- m == mat.length
- n == mat[i].length
- 1 <= m, n <= 10^4^
- 1 <= m * n <= 10^4^
- mat[i][j] is either 0 or 1.
- There is at least one 0 in mat.

# Approach
## Breadth First Search
