---
title: 0 1 Matrix
description: Given an m x n binary matrix mat, return the distance of the nearest 0 for each cell.
published: true
date: 2022-05-27T18:07:19.198Z
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
You can think of the matrix as a graph. There are row * col vertices. There are a maximum of 4 * row * col edges. 

The graph is undirected and unweighted.

We want to find the shortest path between 1 and 0s for each 0 in the graph, which is breadth first search. 

Usually BFS has one source node.