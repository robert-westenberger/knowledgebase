---
title: Binary Search
description: 
published: true
date: 2023-03-18T21:12:01.924Z
tags: algorithms, binary-search, search-algorithms
editor: markdown
---

If an array is already sorted, it is possible to perform a search in $O(\log n)$ time. 

# Method 1
```
int a = 0, b = n-1;
while (a <= b) {
  int k = (a+b)/2;
  if (array[k] == x) {
    // x found at index k
  }
  if (array[k] > x) b = k-1;
  else a = k+1;
}
```