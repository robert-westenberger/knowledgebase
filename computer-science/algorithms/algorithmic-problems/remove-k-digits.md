---
title: Remove K Digits
description: Given string num representing a non-negative integer num, and an integer k, return the smallest possible integer after removing k digits from num.
published: true
date: 2022-05-07T20:02:59.857Z
tags: algorithms, stack
editor: markdown
---

# Problem
Given string num representing a non-negative integer `num`, and an integer `k`, return the smallest possible integer after removing `k` digits from `num`.
## Constraints
- $1 \le k \le \text{num.length} \le 10^5$
- `num` constits of only digits
- `num` does not have any leading zeros except for the zero itself.

## Examples
**Input**: num = "1432219", k = 3
**Output**: "1219"
**Explanation**: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.

**Input**: num = "10200", k = 1
**Output**: "200"
**Explanation**: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.

**Input**: num = "10200", k = 1
**Output**: "200"
**Explanation**: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.

# Approach
## Using Stack
The length of the given string will be `n`, so the result string will contain the length of `n-k`.

We ensure that the output string contains minimum values at their high weightage positions by using a stack.

1. Return $0$ if $k \ge n$, return `num` if $k=0$.

2. Create a stack and iterate through `num` string and push the value at that position if it is greater than the top element of the stack.

3. Iterate through the num string and if the integer value at that position is less than the top of the stack we will pop the stack and decrement k until we reach the condition where the top of the stack is less than the value we are looking at(while $k>0$) (by this we are making sure that most significant positions of the result are filled with minimum values).

4. If the $k$ is still greater than $0$ we will pop stack until $k$ becomes $0$.
5. Append the elements in the stack to the result string.
6. Delete leading zeroes from the result string.
