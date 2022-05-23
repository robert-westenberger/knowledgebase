---
title: Find Connected Cells in a Matrix
description: 
published: true
date: 2022-05-23T00:28:24.509Z
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

# Algorithm
## Depth First Search
We iterate over the grid. When we find an island, we use depth first search to find all of the connected pieces of the island. As we traverse the island, we set the `1`s to `0` to prevent researching the same piece of land twice.
### Implementation(Javascript)
```
const maxAreaOfIsland = (grid) => {
    let answer = 0;

    const numRows = grid.length;
    const numCols = grid[0].length;

    const traverse = (row, col) => {
        // if outside of map, return 0..
        if (row < 0 || col < 0 || row >= numRows || col >= numCols || !grid[row][col]) {
            return 0;
        }
        grid[row][col] = 0;
        return 1 + traverse(row+1, col) + traverse(row-1, col) + traverse(row, col+1) + traverse(row, col-1);
    }

    for (let row = 0; row < numRows; row++) {
        for (let col=0; col < numCols; col++) {
            if (grid[row][col] === 1) {
                answer = Math.max(answer, traverse(row, col));
            }
        }
    }
    return answer;
}
```