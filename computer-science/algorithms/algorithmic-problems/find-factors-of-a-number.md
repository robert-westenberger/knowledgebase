---
title: Find Factors of a Number
description: 
published: true
date: 2022-04-29T15:09:06.348Z
tags: algorithms
editor: markdown
---

# Problem
Create a function that takes an integer $n>1$ and returns an array with all of the integer's divisors (except for 1 and the number itself), from smallest to largest. 

## Solution 1 (Javascript)
```
function divisors(integer) {
  const limit = integer / 2;
  const returnVal = [];
  for (i = 2; i <= limit; i++) {
    if ((integer % i) === 0) {
      returnVal.push(i);
    }
  }
  return returnVal.length ? returnVal : `${integer} is prime`
};
```
## Solution 2 (Javascript)
```
function divisors(integer) {
  const returnVal = [];
  for (let i=2; i<= Math.sqrt(integer); i++) {
    if ((integer % i) === 0) {
        returnVal.push(i);
      if ((i !== (integer / i))) {
        returnVal.push(integer / i);
      }
    }
  }
  return returnVal.length ? returnVal.sort((a,b)=>a-b) : `${integer} is prime`;
}
```
Above solution sets a limit at the root of the integer. Factors that are greater than the root are found by testing whether the smaller numbers evenly divide the integer. 

For example, the square root of $147$ is $12.124355653$,
and it's factors (not including 1 and itself) are $3$, $7$, $21$, and $49$. In order to get $49$, when we reach $3$ we take advantage of the fact that we already know that $3$ is a factor, and get it's companion number $49$ ($3 * 49 = 147$).