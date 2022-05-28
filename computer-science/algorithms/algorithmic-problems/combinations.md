---
title: Combinations
description: 
published: true
date: 2022-05-28T21:54:41.111Z
tags: algorithms, backtracking
editor: markdown
---

# Problem
Given two integers n and k, return all possible combinations of k numbers out of the range [1, n].

You may return the answer in any order.

## Constraints
- 1 <= n <= 20
- 1 <= k <= n

## Examples

**Input**: n = 4, k = 2
**Output**:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]

# Approach
## Backtracking
We use backtracking to incrementally build candidates. Starting wtih an empty list, from 1 to n, we push 1 into the list, make a recursive call, where in that call we will be pushing 2 to n into the list. Then we backtrack, popping the element we just added and continuing the loop. 

So, in the case of n = 4 k = 2, in the toplevel function, 
we recurse 4 times. 
[1]
[2]
[3]
[4]

At the next level, of recursion, we get
[1,2]
[1,3]
[1,4]
[2.3]
[2,4]
[3,4]

### Implementation (Javascript)
```
var combine = function(n, k) {
    const answers = [];
    const backtrack = (remain, combination, next ,level) => {
    
 
        if (remain === 0) {
            answers.push(combination);
            return;
        }
        for (let i = next; i <= n; i++){
                combination.push(i);
                backtrack(remain-1, [...combination], i+1, level+1);
                combination.pop();
            }
    }
    backtrack(k, [], 1, 0);

    return answers;
};
```
