---
title: Loop Invariants
description: 
published: true
date: 2021-08-22T02:08:31.933Z
tags: computer-science, mathematics, discrete-mathematics, algorithms
editor: markdown
---

A **loop invariant** is a logical assertion that is true before and after each iteration of a loop. 

# Three Necessary Parts of a Loop Invariant
* **Initialization** - It must be true prior to the first iteration of the loop
* **Maintenance** If its true before an iteration, it remains true before the next iteration
* **Termination** - When the loop terminates, the invariant gives us a useful property
that helps show that the algorithm is correct.




## Example: Insertion Sort

**Insertion Sort**
<pre>
<strong>Input:</strong> A sequence of <i>n</i> numbers  [a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>]
<strong>Output:</strong> A permutation (reordering) [a<super>'</super><sub>1</sub>, a<super>'</super><sub>2</sub>, ..., a<super>'</super><sub>n</sub>] of the input sequence
such that a<super>'</super><sub>1</sub> ≤ a<super>'</super><sub>2</sub> ≤ ... ≤ a<super>'</super><sub>n</sub>
</pre>

<pre>
1 <strong>for</strong> j=2 <strong>to</strong> A.length
2   key = A[j]
3   // Insert A[j] into the sorted sequence A[1..j-1]
4   i = j-1
5   <strong>while</strong> i > 0 and A[i] > key
6     A[i + 1] = A[i]
7     i = i - 1
8   A[i+1] = key
</pre>

For the above, the loop invariant would be
$$
\text{At the start of each iteration of the for loop of lines } 1-8\text{, the subarray} A[1 \ldots j-1] \text{consists of the elements originally in} A[1 \ldots j-1] \text{, but in sorted order.}
$$
At the start of each iteration of the for loop of lines $1-8$, the subarray $A[1 \ldots j-1]$ consists of the elements originally in $A[1 \ldots j-1]$, but in sorted order.