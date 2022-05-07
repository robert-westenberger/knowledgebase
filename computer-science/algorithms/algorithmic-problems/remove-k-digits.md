---
title: Remove K Digits
description: Given string num representing a non-negative integer num, and an integer k, return the smallest possible integer after removing k digits from num.
published: true
date: 2022-05-07T19:52:28.158Z
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

