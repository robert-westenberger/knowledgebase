---
title: Longest Substring Without Repeating Characters
description: 
published: true
date: 2022-05-01T18:36:09.207Z
tags: algorithms, sliding-window-technique
editor: markdown
---

# Problem
Given a string `s`, find the length of the longest substring without repeating characters.

## Constraints
$0 \le \text{s.length} \le 5 \cdot 10^4$
$s$ consists of English letters, digits, symbols and spaces.
## Examples
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

## Approach
### Sliding Window Technique
- Run a loop from 
