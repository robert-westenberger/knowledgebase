---
title: Arrays
description: 
published: true
date: 2022-05-01T23:06:06.230Z
tags: data-structures, arrays
editor: markdown
---


# Overview
Structure of fixed-size data records such that each element can be efficiently located by its index.
## Advantages and Disadvantages
### Advantages (of contiguously-allocated arrays)
* Constant-time access given the index: Since the index of each element is mapped directly to a memory address, we can access arbitrary data items instnatly provided we know the index.
* Space efficiency - Arrays consist purely of data, no space is wasted with links or other formatting information. End of record information is not needed because arrays are built from fixed-size records. 
* Memory locality - Arrays are easily iterated through. Physical continuity between successive data accesses helps exploit the high-speed cache memory on modern computer architectures.

### Disadvantages (of contiguously-allocated arrays)
We can't adjust their size in the middle of a program's execution.

Because of the need for continuous chunks of memory, sufficient storage space must be allocated at one time. Therefore, if the array has to be expanded, we need to find and reallocate a larger space first, and then copy all the data over; time complexity $O(n)$.

## Dynamically Allocated Arrays
An array that starts as a fixed size array, and whose size is doubled each time we run out of space. The doubling process involves allocating a new contiguous array of size $2m$, copying the contents of the old array to the lower half of the new one, and returning the space used by the old array to the storage allocation sy stem.

### Number of Movements In A Dynamically Allocated Array
The total movements $M$ of all elements (if half the elements move once, a quarter of the elements twice, etc) in a dynamically allocated array is given as follows

$$
M=\sum_{i=1}^{\lg n} i \cdot n / 2^{i}=n \sum_{i=1}^{\lg n} i / 2^{i} \leq n \sum_{i=1}^{\infty} i / 2^{i}=2 n
$$

The first inserted element will have been recopied when the array expands after the first, second, fourth, eighth.. insertions. It will take $\log _{2} n$ doublings until the array gets to have $n$ positions. Most elements do not suffer much upheaval.The $(n / 2+1) \mathrm{st}$ through $n$th elements will most at most once and might never have to move at all.

Thus, each of the $n$ elements move only two times on average, and the total work of managing the dynamic array is the same $O(n)$ as it would have been if a single array of sufficient size had been allocated in advance.

The primary thing lost using dynamic arrays is the guarantee that each array access takes constnat time in the worst case. Now all queries will be fast except for those that trigger array doubling.