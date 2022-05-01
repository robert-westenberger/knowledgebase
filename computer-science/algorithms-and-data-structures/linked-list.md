---
title: Linked List
description: 
published: true
date: 2022-05-01T23:10:35.936Z
tags: data-structures, linked-lists
editor: markdown
---

# Overview
## Advantages and Disadvantages
### Advantages
- Elements are not continuous, so they are easy to expand. If you know the parent and child of a node, insertion or deletion can be done in constant time. 
- Overflow on linked structures never occurs unless the memory is actually full.
- Insertion and deletion are simpler than for static arrays. 
- With large records, moving pointers is easier and faster than moving the items themselves.
### Disadvantages
- Since storage space is not continuous, you can't calculate the address of corresponding elements according to an index, so you can't access it randomly. 
- Because each element must store a pointer to the location of it's parent and/or child nodes, it will consume more storage space. 


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

### Basic Operations
#### Traversal
##### Iterative
```
```
#### Insertion into a List
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

#### Deletion From a List
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