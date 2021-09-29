---
title: Binary Search Trees
description: 
published: true
date: 2021-09-29T17:37:00.931Z
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
Search
Minimum
Maximum
Predecessor
Successor
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

