---
title: WIP Data Structures
description: 
published: true
date: 2021-09-02T17:36:49.466Z
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

## Advantages (of contiguously-allocated arrays)
* Constant-time access given the index: Since the index of each element is mapped directly to a memory address, we can access arbitrary data items instnatly provided we know the index.
* Space efficiency - Arrays consist purely of data, no space is wasted with links or other formatting information. End of record information is not needed because arrays are built from fixed-size records. 
* Memory locality - Arrays are easily iterated through. Physical continuity between successive data accesses helps exploit the high-speed cache memory on modern computer architectures.

## Disadvantages (of contiguously-allocated arrays)
We can't adjust their size in the middle of a program's execution.

## Array
Structures of fixed-size data records such that each element can be efficiently located by its index.

### Dynamically Allocated Arrays
An array that starts as a fixed size array, and whose size is doubled each time we run out of space. The doubling process involves allocating a new contiguous array of size $2m$, copying the contents of the old array to the lower half of the new one, and returning the space used by the old array to the storage allocation sy stem.

#### Number of Movements In A Dynamically Allocated Array
The total movements $M$ of all elements (if half the elements move once, a quarter of the elements twice, etc) in a dynamically allocated array is given as follows

$$
M=\sum_{i=1}^{\lg n} i \cdot n / 2^{i}=n \sum_{i=1}^{\lg n} i / 2^{i} \leq n \sum_{i=1}^{\infty} i / 2^{i}=2 n
$$

The first inserted element will have been recopied when the array expands after the first, second, fourth, eighth.. insertions. It will take $\log _{2} n$ doublings until the array gets to have $n$ positions. Most elements do not suffer much upheaval.The $(n / 2+1) \mathrm{st}$ through $n$th elements will most at most once and might never have to move at all.

Thus, each of the $n$ elements move only two times on average, and the total work of managing the dynamic array is the same $O(n)$ as it would have been if a single array of sufficient size had been allocated in advance.

The primary thing lost using dynamic arrays is the guarantee that each array access takes constnat time in the worst case. Now all queries will be fast except for those that trigger array doubling.

# Linked Data Structures
Composed of distinct chunks of memory bound together by pointers, and include lists, trees, and graph adjacency lists.

## Advantages
- Overflow on linked structures never occurs unless the memory is actually full.
- Insertion and deletion are simpler than for static arrays. 
- With large records, moving pointers is easier and faster than moving the items themselves.


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

### Insertion into a List
There is no need to maintain the list in any particular order, since the "order" is maintained by each individual list item's pointer property. Insertion at the beginning of the list avoids any need to traverse the list, but does require us to update the pointer (denoted *l*)

```
void insert_list(list **l, item_type x) {
	list *p; /* temporary pointer */
	p = malloc(sizeof(list));
	p->item = x;
	p->next = *l;
	*l = p;
}
```

> The malloc function allocates a chunk of memory of sufficient size for a new node to contain *x*.
{.is-info}

> The double star `**l` denotes that l is a pointer to a pointer to a list node. So the last line `*l=p;` copies p to the place pointed to by l, which is the external variable maintaining access to the head of the list. 
{.is-info}

### Deletion From a List
To delete from a singly linked list, we must find a pointer to the *predecessor* of the item to be deleted. 

```
list *item_ahead(list *l, list *x) {
	if ((l == NULL) || (l->next == NULL)) {
		return(NULL);
	}
	if ((l->next) == x) {
		return(l);
	} else {
		return(item_ahead(l->next, x));
	}
}
```
The predecessor's (the node that points to the node to be deleted) pointer to the next item in the list needs to be updated because its current one is about to be deleted.

```
void delete_list(list **l, list **x) {
	list *p; /* item pointer */
	list *pred; /* predecessor pointer */
	p = *l;
	pred = item_ahead(*l, *x);
	
  if (pred == NULL) { /* splice out of list */
		*l = p->next;
	} else {
		pred->next = (*x)->next;
	}
	free(*x); /* free memory used by node */
}
```

Special care must be taken to reset the pointer to the head of list (*l*) when the first element is deleted.

C requires explicit deallocation of memory, so we must *free* the deleted node after we are finished with it in order to return the memory to the system. This leaves the incoming pointer as a dangling reference to a location that no longer exists, so care must be taken not to use this pointer again.

