---
title: WIP Data Structures
description: 
published: true
date: 2021-09-07T18:20:16.263Z
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

# Containers
The term **container** denotes an abstract data type that permits storage and retrieval of data items independent of content. 

Containers are distinguished by the particular retrieval order they support.

## Stacks
### Retrieval Order
**Last-in, first-out (LIFO)** order.
### When to use
Use them when retrieval order doesn't matter, such as when processing batch jobs. 
### Operations
The put and get operations are usually called push and pop.
- Push(x,s): Insert item *x* at the top of the stack *s*.
- Pop(s): Return (and remove) the top item of stack *s*. 

## Queues
### Retrieval Order
**First-in, first-out (FIFO) order.**
### When to use
When order is important. 
### Operations
The put and get operations are usually called enqueue and dequeue
- Enqueue(x,q): Insert item x at the back of queue q.
- Dequeue(q): Return (and remove) the front item from queue q.

# Dictionaries
Permits access to data items by content. 
## Primary Operations
- Search(D,k) – Given a search key k, return a pointer to the element in dictionary D whose key value is k, if one exists.
- Insert(D,x) – Given a data item x, add it to the dictionary D.
- Delete(D,x) – Given a pointer x to a given data item in the dictionary D, remove it from D.

Certain dictionary data structures also efficiently support other useful operations:

- Max(D) or Min(D) – Retrieve the item with the largest (or smallest) key from D. This enables the dictionary to serve as a priority queue.
- Predecessor(D,x) or Successor(D,x) – Retrieve the item from D whose key is immediately before (or after) item x in sorted order. These enable us to iterate through the elements of the data structure in sorted order.


# Binary Trees
Basic operations supported by binary trees are searching, traversal, insertion, and deletion.
## Rooted Binary Tree
A rooted binary tree is recursively defined as being either

1. Empty
2. Consisting of a node called the **root**, together with two rooted binary trees called the left and right subtrees, respectively. 

Order matters among "sibling" nodes in rooted trees. The left subtree is different from the right. 
## Binary Search Trees
A binary search tree labels each node in a binary tree with a single key such that for any node labeled $x$, all nodes in the left subtree of $x$ have keys $\lt x$ while all nodes in the right subtree have keys $\gt x$.


### Implementation
Binary tree nodes have the following fields
* Left pointer
* Right pointer
* Parent pointer (optional)
```
typedef struct tree {
	item_type item; /* data item */
	struct tree *parent; /* pointer to parent */
	struct tree *left; /* pointer to left child */
	struct tree *right; /* pointer to right child */
}
```

### Searching
The BST labeling scheme uniquely identifies where each key is located. The algorithm is as follows:

1. Start at the root
2. Unless it contains the query key $x$, proceed either left or right depnding upon whether $x$ occurs before or after the root key. 


The recursive nature of BST's allows for a recursive search algorithm
```
tree *search_tree(tree *l, item_type x) {
	if (l == NULL) {
		return(NULL);
	}
	if (l->item == x) {
		return(l);
	}
	if (x < l->item) {
		return(search_tree(l->left, x));
	} else {
		return(search_tree(l->right, x));
	}
}
```

The above algorithm runs in $O(h)$, where $h$ denotes the height of the tree.

### Finding minimum and maximum elements
The smallest key in a BST must reside in the left subtree of the root by definition. 
```
tree *find_minimum(tree *t) {
	tree *min; /* pointer to minimum */
	if (t == NULL) {
		return(NULL);
	}
	min = t;
	while (min->left != NULL) {
		min = min->left;
	}
	return(min);
}
```

### Traversal
Visiting every node in a RBT is an important part of many algorithms. It is a special case of traversing all the nodes and edges in a graph.

BST's make it easy to report labels in sorted order. All keys smaller than the root must lie in the left subtree of the root, and all keys bigger than the root in the right subtree. Visiting the nodes recursively produces an in-order traveersal of the search tree
```
void traverse_tree(tree *l) {
	if (l != NULL) {
		traverse_tree(l->left);
		process_item(l->item);
		traverse_tree(l->right);
	}
}
```

Each item is processed only once during the course of traversal, so it runs in $O(n)$ time, where $n$ is the number of nodes in the tree.

Changing the position of the `process_item` call relative to the traversals of the left and right subtrees changes the order of the traversal. 
* Processing the item first yields a **pre-order traversal**
* Processing the item last yields a **post-order traversal**

### Insertion
There is exactly one place to insert an item $x$ into a BST $T$. 

This implementation uses recursion to combine the search and node inseration stages of key insertion. The three arguments to insert_tree are 
1. A pointer $l$ to the pointer linking the search subtree to the rest of the tree
2. The key $x$ to be inserted
3. A parent pointer to the parent node containing $l$.  

```
void insert_tree(tree **l, item_type x, tree *parent) {
	
  tree *p; /* temporary pointer */

	if (*l == NULL) {
		p = malloc(sizeof(tree));
		p->item = x;
		p->left = p->right = NULL;
		p->parent = parent;
		*l = p;
		return;
	}
	if (x < (*l)->item) {
		insert_tree(&((*l)->left), x, *l);
	} else {
		insert_tree(&((*l)->right), x, *l);
	}
}
```
The node is allocated and linked in after hitting the NULL pointer. Note that we pass the pointer to the appropriate left/right poitner int he node during the search, so the assignment `*l=p;` links the new node into the tree.

### Deletion
![bst_deletion.png](/bst_deletion.png)

The above image depicts deleting tree nodes with 0, 1, and 2 children.

#### Deleting a leaf node
Simply clear the pointer to the given node. We don't have to worry about relinking any other nodes.

#### Deleting node with 1 child
The child of the node to be deleted is linked to the deleted node's parent. 

#### Deleting node with 2 children
Relabel the deleted node with the key of its immediate successor in sorted order. This successor must be the smallest value in the right subtree, specifically the left-most decendant in the right subtree `p`. Moving this descendant to the point of deletion results in a properly labeled binary search tree, and reduces our deletion problem to physically removing a node with at most one child. 

# Priority Queues
## Primary Operations
- Insert(Q, x) – Given item x, insert it into the priority queue Q.
- Find-Minimum(Q) or Find-Maximum(Q) - Return a pointer to the item whose key value is smallest (or largest) among all keys in priority queue Q.
- Delete-Minimum(Q) or Delete-Maximum(Q) - Remove the item whose key value is minimum (or maximum) from priority queue Q.


# Hashing
The key idea of hashing is to represent a large object (be it a key, string, or substring) by a single number. 

A **hash function** is a mathematical function that maps keys to integers. 

The first step of the hash function is usually to map each key (here the string $S$) to a big integer. Let $\alpha$ be the size of the alphabet on which $S$ is written. Let `char(c)` be a function that maps each symbol of the alphabet to a unique integer from $0$ to $\alpha - 1$. The function

$$
H(S)=\alpha^{|S|}+\sum_{i=0}^{|S|-1} \alpha^{|S|-(i+1)} \times \operatorname{char}\left(s_{i}\right)
$$

maps each string to a unique (but large) integer by treating the characters of the string as "digits" in a base-$\alpha$ number system.

This creates unique identifier numbers, but they are so large they will quickly exceed the number of desired slots in our hash table (denoted by $m$). We must reduce this number to an integer between $0$ and $m-1$, by taking the remainder $H^{\prime}(S)=H(S) \bmod m$. This works on the same principle as a roulette wheel. The ball travels a long distance, around the circumference-$m$ wheel $\lfloor H(S) / m\rfloor$ times before settlign down to a random bin. 

## Real World Problems to Which Hashing Is an Elegant Solution
* Is a given document unique within a large corpus? - We can hash the document $D$ to an integer, and compare $H(D)$ to the hash codes of the rest of the corpus. Only if there is a collision might $D$ be a possible duplicate. 
* Is part of this document plagiarized? - (how? TODO: look into this one more)
* Convince someone a file isn't changed -  (how? TODO: look into this one more)... this one makes use of cryptographic hashing. 
## Collision Resolution
Two distinct keys will at least occasionally hash to the same value. There are two different approaches for maintaining a hash table:

* **Chaining**  represents a hash table as an array of $m$ linked lists ("buckets"). The $i$th list will contain all the items that hash to the value $i$. Search, insertion, and deletion thus reduce to the corresponding problem in linked lists. If the $n$ keys are distributed uniformly in a table, each list will contain roughly $n/m$ elements, making them a constant size when $m \approx n$. 

* **Open addressing** maintains the hash table as a simple array of elements (not buckets). EAch cell is initialized to null. On each insertion, we check to see whether the desired cell is empty; if so, we insert the item there. If the cell is already occupied, we must find some other place to put the item. The simplest possibilty (called **sequential probing**) inserts the item into the next open cell in the table. 

## Canocicalization

