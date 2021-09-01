---
title: WIP Data Structures
description: 
published: true
date: 2021-09-01T18:52:48.518Z
tags: data-structures
editor: markdown
---

Will focus on three fundamental abstract data types

1) Containers
2) Dictionaries
3) Priority Queues

and see how they can be implemented with arrays and lists.

# Contiguous Data Structures
Composed of single slabs of memory, and include arrays, matrices, heaps, and hash tables

## Array
Structures of fixed-size data records such that each element can be efficiently located by its index.

### Advantages (of contiguously-allocated arrays)
* Constant-time access given the index: Since the index of each element is mapped directly to a memory address, we can access arbitrary data items instnatly provided we know the index.
* Space efficiency - Arrays consist purely of data, no space is wasted with links or other formatting information. End of record information is not needed because arrays are built from fixed-size records. 
* Memory locality - Arrays are easily iterated through. Physical continuity between successive data accesses helps exploit the high-speed cache memory on modern computer architectures.

### Disadvantages (of contiguously-allocated arrays)
We can't adjust their size in the middle of a program's execution.

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

# Linked Data Structures
Composed of distinct chunks of memory bound together by pointers, and include lists, trees, and graph adjacency lists.

## Pointers
Pointers represent the address of a location in memory. A variable storing a pointer to a given data item can provide more freedom than storying a copy of the item itself. 

### Pointers in C
A pointer **p** is assumed to give the address in memory where a particular chunk of data is located. Pointers in **C** have types declared at compile time, denoting the data type of the items they can point to. We use ***p** to denote the item that is pointed to by pointer **p**, and **&x** to denote the address of (pointer to) a particular variable **x**. A special **NULL** pointer value is used to denote structure-terminating or unassigned pointers.
## Linked Data Structure Properties
All linked data structures share certain properties, as revealed by the following linked list type declaration:

<pre>
typedef struct list {
	item_type item; /* data item */
 	struct list *next; /* point to successor */
} list;
</pre>

* Each node in our data structure contains one or more data fields (in this case *item*) that retain the data we need to store.

* Each node contains a pointer field to at least one other node (here *next*). This means that much of the space used in linked data structures has to be used for pointers, not data.

* We need a pointer to the head of the structure, so we know where to access it.



## List 
The **list** is the simplest linked structure (pseudocode given in the preceding section). The three basic operations supported by lists are searching, insertion, and deletion. In **doubly-linked lists**, each node points to both its predecessor and successor element.

### Searching a List

