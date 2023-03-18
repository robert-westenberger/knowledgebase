---
title: Binary Search
description: 
published: true
date: 2023-03-18T21:13:03.660Z
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

At each step, the search checks the middle element of the active region. If the middle element is the target element, the search terminates. Otherwise, the search recursively continues to the left or right half of the region, depending on the value of the middle element.

# Method 2