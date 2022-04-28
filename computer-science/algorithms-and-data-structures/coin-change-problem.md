---
title: Coin Change Problem
description: 
published: true
date: 2022-04-28T15:19:23.098Z
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

#### Subproblem tables generated
Note that for the below generated tables, the rows are for arrays of coins, starting from no coins, and adding another coin on each row until we have an array of all the coins.

For example, if we have coins `[1, 2, 5]`, we would have 
```
[]
[1]
[1, 2]
[1, 2, 5]
```

The columns are series of sequential integers from `0` to `n` where `n` is the amount of money. So if we were trying to calculate change for `5`, the columns from left to right would be 
```
0 1 2 3 4 5
```
##### Making change for `4` with a `1` and a `2` coin.

```
[ 
  [ 1, 0, 0, 0, 0 ], 
  [ 1, 1, 1, 1, 1 ], 
  [ 1, 1, 2, 2, 3 ]
]
```
##### Making change for `10` with a `5`, `2`, and `3` coin
```
[ 
  [ 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ],
  [ 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1 ],
  [ 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 2 ],
  [ 1, 0, 1, 1, 1, 2, 2, 2, 3, 3, 4 ] 
]
```
#### Implementation 1 (Javascript)
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
#### Implementation 2 (Javascript)
```
var countChange = function(money, coins) {
  if(money < 0 || coins.length === 0)
    return 0
  else if(money === 0)
    return 1
  else
    return countChange(money - coins[0], coins) + countChange(money, coins.slice(1))
}
```
For this recursive implementation, starting from the amount of money we are checking for and the total set of coins, we return `0` if money is less than `0` or the amount of `coins` is `0`, since we can't make change for a negative amount or if we have no coins. 

If money is `0`, we return `1` because there is exactly `1` way to make change for `0`. 

Otherwise, 
#### Implementation 3 (Javascript) 
```
let countChange = (amount, coins) => {
  let [coin, ...rest] = coins
  if (!coin)       return 0
  if (amount <  0) return 0
  if (amount == 0) return 1
  return countChange(amount - coin, coins) + 
         countChange(amount, rest)
}
```