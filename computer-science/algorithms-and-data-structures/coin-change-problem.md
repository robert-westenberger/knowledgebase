---
title: Coin Change Problem
description: 
published: true
date: 2022-04-27T17:31:14.668Z
tags: algorithms, dynamic-programming
editor: markdown
---

# Problem
Given a list of coins i.e 1 cents, 5 cents and 10 cents, can you determine the total number of combinations of the coins in the given list to make up the number N?

This is a type of **knapsack** problem.
## Example
### Example 1
Suppose you are given the coins 1 cent, 5 cents, and 10 cents with N = 8 cents, what are the total number of combinations of the coins you can arrange to obtain 8 cents. 
```
Input: N=8
        Coins : 1, 5, 10
Output: 2

Explanation: 
1 way: 
      1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 = 8 cents.
2 way:
      1 + 1 + 1 + 5 = 8 cents.
```      
### Example 2
Suppose you are given the coins 1 cent, 5 cents, and 10 cents with N = 10 cents, what are the total number of combinations of the coins you can arrange to obtain 10 cents. 
```
Input : N=10
        Coins : 1, 5, 10
Output : 4
Explanation: 
1 way: 
   1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 = 10 cents.
2 way: 
   1 + 1 + 1 + 1 + 1 + 5 = 10 cents.
3 way: 
   5 + 5 = 10 cents.
4 way: 
   10 cents = 10 cents.
```
# Approach
## Dynamic Programming
Dynamic programming can be used to tackle this problem. Recall that dynamic programming is simplifying a complicated problem by breaking it down into simpler sub-problems in a recursive manner. 

### The subproblem
We need to calculate the number of ways to make change using the given coins for each integer between `0` and `n`, where `n` is the amount we are making change for. 

The subproblems can be arranged in a two dimensional table. The value `arr[i][j]` in our array represents the number of possible ways that a sum `j` can be made using the first `i` coins only.

#### Implementation (Javascript)
```
var countChange = function(money, coins) {
  const subProbsArray = new Array(coins.length + 1).fill(null).map(() => new Array(money +1).fill(null).map(() => 0));
  // 1 way to make change for 0...
  for (let i = 0; i < coins.length + 1; i++){
    subProbsArray[i][0] = 1;
  }
  for (let i = 1; i < coins.length + 1; i++) {
    for (let j = 1; j < money + 1; j++) {
      subProbsArray[i][j] = subProbsArray[i - 1][j] + 
        (j >= coins[i-1] ? subProbsArray[i][j - coins[i -1]] : 0);
    }
  }
  return subProbsArray[coins.length][money];
}
```