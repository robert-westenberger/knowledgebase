---
title: Generate Valid Parentheses
description: 
published: true
date: 2022-05-01T00:28:14.606Z
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
### Base Case
The base case is when the length of the current string we are building is $n \cdot 2$. 


The longest the string can possibly be, for $n$ parens, is $n\cdot2$. When we are building a possible string of valid parens, at each level of recursion, if it's length is $n \cdot 2$ we know it has $n$ valid parens and we can add it to our list of answers.
### First Recursive Path - Open Parentheses
Our first path of recursion adds an opening parens, if one can still be added. This path will be called exactly $n$ times.
### Second Recursive Path - Close Parentheses
### Implementation(Javascript)
```
const backtrack = (outputArray, currString, open, close, max, level = 0) => {
  // base case
  if (currString.length === max * 2) {
    outputArray.push(currString);
    return;
  }
  if (open < max) {
    backtrack(outputArray, currString + "(", open + 1, close, max, level + 1);
  }
  if (close < open) {
    backtrack(outputArray, currString + ")", open, close + 1, max, level + 1);
  }
}
const generateParentheses = (n) => {
  const outputArray = [];
  backtrack(outputArray, "", 0, 0, n);
  return outputArray;
}
```