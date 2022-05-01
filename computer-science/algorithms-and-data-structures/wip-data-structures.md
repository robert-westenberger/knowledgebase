---
title: WIP Data Structures
description: 
published: true
date: 2022-05-01T23:04:57.317Z
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

See [Arrays](/computer-science/algorithms-and-data-structures/arrays)

# Linked Data Structures
Composed of distinct chunks of memory bound together by pointers, and include lists, trees, and graph adjacency lists.

See [Linked Lists](/computer-science/algorithms-and-data-structures/linked-list)



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


# Red-Black Tree
A red-black tree is a kind of self-balancing tree structure. Height-balancing the tree will prevent issues caused by relying purely on insertion order to build and maintain the tree (in the worst case, we can get a skinny tree whose height is the same as the number of nodes in the tree). 

A red-black tree satisfies the following **red-black properties**:
1. Every node is either red or black.
2. The root is black.
3. Every leaf is black.
4. If a node is red, then both its children are black.
5. For each node, all simple paths from the node to descendant leaves contain the same number of black nodes.

## Rotations (On Insertion and Deletion)
Every time elements are inserted or deleted, we must change some colors and the pointer structure of the tree to prevent violation of any of the red-black properties.

The pointer structure of the tree is changed through **rotation**, which is a local operation in a search tree that preserves the binary-search-tree property.


![rbt_1.png](/rbt_1.png)
### Left Rotation
In left rotation, we assume that the right child is not null.
![rbt_left_before.png](/rbt_left_after.png)

![left_rotation_rbt.gif](/left_rotation_rbt.gif)

![rbt_left_after.png](/rbt_left_after.png)
After applying left rotation on the node x, the node y will become the new root of the subtree and its left child will be x. And the previous left child of y will now become the right child of x.


### Right Rotation
In right rotation, we assume that the left child is not null.


![rbt_right_before.png](/rbt_left_after.png)


![right_rotation_rbt.gif](/right_rotation_rbt.gif)


![rbt_right_after.png](/rbt_left_after.png)
Right rotation on the node y will make x the root of the tree, y will become x's right child. And the previous right child of x will now become the left child of y.

## Insertion
Insert can introduce violations of 2 and 4 of the red-black properties. If it is 2, its because the new node is the root and it's red. If its property 4, its because both the new node and it's parent are red.

## Insertion Fixup
After a new node is inserted (always red, unless the tree was previously empty), the colors and structure of the tree needs to change to maintain the red-black properties.

## Deletion
### Delete Algorithm
1. Save a reference to the deleted node's color as originalColor.
2. If the left child of the deleted node is NULL
	a. assign its right child to $x$.
  b. Transplant the node to be deleted with $x$.
3. Else if the right child of the deleted node is NULL
	a. Assign its right child to $x$.
  b. Transplant the node to be deleted with $x$.
4. Else ( node has two children )
	a. Assign the minimum of the right subtree of the node to be deleted to $y$.
  b. Save a reference to $y$'s color as originalColor.
  c. Assign the right child of $y$ into $x$.
  d. If $y$ is a child of the node to be deleted, then set the parent of $x$ as $y$.
  e. Else, transplant $y$ with the right child of $y$.
  f. Transplant node to be deleted with $y$.
  g. Set the color of y to originalColor.
5. If originalColor is black, call the delete fixup procedure.
### Delete Fixup Algorithm
This algorithm is called when a black node is deleted, because that violates the black depth property of the red black tree.

## Node 
```
typedef struct RedBlackTreeNode {
    int item;
    bool color; /* 0 black 1 red */
    struct RedBlackTreeNode *parent;
    struct RedBlackTreeNode *left;
    struct RedBlackTreeNode *right;
} RedBlackTreeNode;
```


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

## Canonicalization
**Canonicalization** (aka **standardization** or **normalization**) is a process for converting data that has more than one possible representation into a "normal" / "standard" / canonical form. 

### Example
Consider a word game that gives you a set of letters $S$, and asks you to find all dictionary words that can be made by reordering them. For example, three words can be made from the four letters in $S=(a, e, k, l)$, namely *kale*, *lake*, and *leak*.

The most straightforward approach is to test each word $d \in D$ against the characters of $S$. This would take linear time in $n$ for each $S$.

We could instead hash every word in $D$ to a string, by sorting the words letters. Now *lake*, *leak*, and *kale* all go to *aekl* which have the same hash. All words with the same letter distribution get hashed to the same bucket. Once you have built this hash table, you can use it for different query sets S. The time for each query will be proportional to the number of matching words in D, which is a lot smaller than n.

The same hash table can be used to calculate which set of $k$ letters can be used to make the most dictionary words. It is just the hash code with the largest number of collisions. 


## Compaction
Also called **fingerprinting**, where we represent large objects by small hash codes. 

### Example
Suppose you want to sort all $n$ books in the library by their contents and not their titles. If we represented each book by its first 100 characters, it would make things a lot quicker. There would be hash collisions involving multiple editions of the same book or plag iarism, but those would be rare. After sorting the 100 character prefixes, collsions can be resolved by comparing the full texts.


# Specialized Data Structures
* String data structures - Character strings are typicaly represented by arrays of characters, perhaps with a special character to mark the end of the string.Suffix trees/arrays are special data structures that preprocess strings to make pattern matching operations faster.
* Geometric data structures - Typically consists of collections of data points and regions. Regions in the plane can be described by polygons, where the boundary of the polygon is a closed chain of line segments. A polygon $P$ can be represented using an array of points $\left(v_{1}, \ldots, v_{n}, v_{1}\right)$, such that $\left(v_{i}, v_{i+1}\right)$ is a segment of the boundary of $P$. Spatial data structures such as $kd$-trees organize poitns and regions by geometric location to support fast search operations.
* Graph data structures - Typically represented using either adjacency matrices or adjacency lists. 
* Set data structures - Subsets of items are typically represented using a dictionary to support fast membership queries. Alternatively, **bit vectors** are boolean arrays such that the $i$th bit is $1$ if $i$ is in the subset.