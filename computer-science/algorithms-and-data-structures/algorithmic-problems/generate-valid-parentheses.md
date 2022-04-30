---
title: Generate Valid Parentheses
description: 
published: true
date: 2022-04-30T22:40:31.328Z
tags: algorithms, parentheses-problems, recursion, bit-manipulation
editor: markdown
---

# Problem
Given $n$ (where $1 \le n \le 8$ ) pairs of parentheses, write a function to generate all combinations of well-formed parentheses. 

## Example 1
```
Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
```
## Example 2
```
Input: n = 1
Output: ["()"]
```

# Approaches
## Bit manipulation + Recursion
### Implementation (Javascript)
```
const generateParentheses = (n) => {
    const answer = [];
    const m = 2 * n;
    const dfs = (pos, open, seq) => {
        if (pos === m) {
            let res = new Array(m);
            for (let i = 0; i < m; i++) {
               res[i] = seq & 1 << i ? "(" : ")"; 
            }
            answer.push(res.join(""))
            return;
        }
        if (open) {
          dfs(pos+1, open-1, seq);  
        }
        if (m - pos > open){
          dfs(pos+1, open+1, seq | 1 << pos);  
        }
    }

    dfs(0, 0, 0);
    return answer;
}
```
## Backtracking