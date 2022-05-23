---
title: Find Connected Cells in a Matrix
description: 
published: true
date: 2022-05-23T00:25:09.577Z
tags: matrix, algorithms, arrays
editor: markdown
---

# Problem
You are given an m x n binary matrix grid. An island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

The area of an island is the number of cells with a value 1 in the island.

Return the maximum area of an island in grid. If there is no island, return 0.

## Constraints
- m == grid.length
- n == grid[i].length
- 1 <= m, n <= 50
- grid[i][j] is either 0 or 1.

## Examples
Input: grid = [
[0,0,1,0,0,0,0,1,0,0,0,0,0],
[0,0,0,0,0,0,0,1,1,1,0,0,0],
[0,1,1,0,1,0,0,0,0,0,0,0,0],
[0,1,0,0,1,1,0,0,**1**,0,**1**,0,0],
[0,1,0,0,1,1,0,0,**1**,**1**,**1**,0,0],
[0,0,0,0,0,0,0,0,0,0,**1**,0,0],
[0,0,0,0,0,0,0,1,1,1,0,0,0],
[0,0,0,0,0,0,0,1,1,0,0,0,0]
]
Output: 6
( Largest island is bolded)