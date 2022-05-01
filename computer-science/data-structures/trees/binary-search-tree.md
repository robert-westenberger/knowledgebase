---
title: Binary Search Trees
description: 
published: true
date: 2021-10-01T17:56:15.522Z
tags: data-structures
editor: markdown
---

# Binary Search Tree Property
The keys in a binary search tree are always stored in such a way to satisfy the binary-search-tree property 
$$
\text{Let} \medspace x \medspace \text {be a node in a binary search tree. If} \medspace y \medspace \text{is a node in the left subtree of } \medspace x  \text{, then} \\
y.\text{key} \le \medspace x \text{.key}. \medspace \text{If} \medspace y \medspace \text{is a node in the right subtree of } \medspace x \text{, then } y.\text{key} \ge \medspace x \text{.key}.
$$
# Operations
## Search
Starting at the root, unless it contains the value we are searching for, recursively search the tree preceding with the left or right child depending on whether the value we are searching for is less or greater than the key of the current node respectively. 
## Minimum
It is the leftmost descendant of the root.
## Maximum
It is the rightmost descendant of the root.
# Predecessor
# Successor
## Insert
To insert a new value `v` into a binary search tree `T`, `v` is put into a new node `z` for which `z.data=v`, `z.left=NULL` and `z.right=NULL`. `T` and some attributes of `z` are modified in such a way that it inserts `z` into an appropriate position in the tree.

### Algorithm
1. Start from the root of the tree
2. Compare the value to be inserted with the value of the current node.
	a. if value inserted $\lt$ value of current node, traverse to the left node of the current node and continue the comparison.
  b. Otherwise, traverse to the right node. 
3. Eventually we reach a leaf node. Set the parent of z to the last node we compared.
4. If the tree was empty, set the root to our newly inserted node.
5. Otherwise, if the value to be inserted is less than its parent node, set parent.left = z.
6. If the value to be inserted is greater than its parent node, set parent.right = z.
  
## Delete
![deleting_subtrees.png](/deleting_subtrees.png)

Above image shows the three possible cases for deleting a node from a tree.

### Deleting leaf node
Clear the pointer to the given node.
### Deleting node with one child
There is one parent and one grandchild, so just directly link the grandparent to the grandchild.
### Deleting node with two children
Relabel this node with the key of its immediate successor in sorted order. This successor must be the smallest value in the right subtree, specifically the leftmost descendant in the right subtree. Moving this to the point of deletion results in a properly labeled binary search tree, and reduces our deletion problem to physically removing a node with at most one child—a case that has been resolved above.