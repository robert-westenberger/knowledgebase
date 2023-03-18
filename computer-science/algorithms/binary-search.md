---
title: Binary Search
description: 
published: true
date: 2023-03-18T22:19:23.390Z
tags: algorithms, binary-search, search-algorithms
editor: markdown
---

If an array is already sorted, it is possible to perform a search in $O(\log n)$ time. 

# Implementations
## Method 1
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

## Method 2
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

# Applications
## Finding the smallest solution
An important use for binary search is to find the position where the value of a function changes. Suppose we wish to find the smallest value $k$ that is a valid soln for a problem. We are given a function $ok(x)$ that returns `true` if $x$ is a valid soln and `false` otherwise. In addition, we know that $ok(x)$ is `false` when $x \lt k$ and `true` when $x \geq k$.

$$
\begin{aligned}
&\text { when } x<k \text { and true when } x \geq k \text {. The situation looks as follows: }\\
&\begin{array}{r|rrrrrrr}
x & 0 & 1 & \cdots & k-1 & k & k+1 & \cdots \\
\hline o k(x) & \text { false } & \text { false } & \cdots & \text { false } & \text { true } & \text { true } & \cdots
\end{array}
\end{aligned}
$$

```
int x = -1;
for (int b = z; b >= 1; b /= 2) {
   while (!ok(x+b)) x += b;
}
int k = x+1;
```

The search finds the largest value of $x$ for which ok $(x)$ is false. Thus, the next value $k=x+1$ is the smallest possible value for which ok $(k)$ is true. The initial jump length $z$ has to be large enough, for example some value for which we know beforehand that ok $(z)$ is true.

The algorithm calls the function ok $O(\log z)$ times, so the total time complexity depends on the function ok. For example, if the function works in $O(n)$ time, the total time complexity is $O(n \log z)$.


## Finding the maximum value
B Search can be used to find the max value for a function that is first increasing and then decreasing. To find a position $k$ s.t. 

- $f(x)<f(x+1)$ when $x<k$, and
- $f(x)>f(x+1)$ when $x \geq k$.

The idea is to use binary search for finding the largest value of $x$ for which $f(x)<f(x+1)$. This implies that $k = x + 1$ because $f(x+1)>f(x+2)$. 

```
int x = -1;
for (int b = z; b >= 1; b /= 2) {
  while (f(x+b) < f(x+b+1)) x += b;
}
int k = x+1;
```