---
title: Binary Trees
description: 
published: true
date: 2022-05-01T23:17:59.146Z
tags: data-structures, trees, binary-trees
editor: markdown
---

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