---
title: Binary Search
description: 
published: true
date: 2023-03-18T22:05:24.162Z
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
```
int k = 0;
for (int b = n/2; b >= 1; b /= 2) {
  while (k+b < n && array[k+b] <= x) k += b;
}
if (array[k] == x) {
  // x found at index k
}
```

An alternative method to implement binary search is based on an efficient way to iterate through the elements of the array. The idea is to make jumps and slow the speed when we get closer to the target element.

The search goes through the array from left to right, and the initial jump length is $n / 2$. At each step, the jump length will be halved: first $n / 4$, then $n / 8$, $n / 16$, etc., until finally the length is 1 . After the jumps, either the target element has been found or we know that it does not appear in the array.

During the search, the variable $b$ contains the current jump length. The time complexity of the algorithm is $O(\log n)$, because the code in the while loop is performed at most twice for each jump length.