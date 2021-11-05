---
title: AVL Tree
description: 
published: true
date: 2021-11-05T19:28:58.989Z
tags: data-structures
editor: markdown
---

# AVL Tree
This is a self-balancing Binary Search Tree, where the difference between the heights of left and right subtrees cannot be more than one for all nodes. 

Most of the BST operations (e.g., search, max, min, insert, delete.. etc) take O(h) time where h is the height of the BST. 

If we make sure that height of the tree remains O(Logn) after every insertion and deletion, then we can guarantee an upper bound of O(Logn) for all these operations. The height of an AVL tree is always O(Logn) where n is the number of nodes in the tree.
## Node Structure
```
typedef struct AVLNode {
    void *data;
    struct AVLNode *left;
    struct AVLNode *right;
    int height;
} AVLNode;
```

## Insertion (Recursive)
1. Start with standard BST insertion. (recursively traverse the tree until the proper location of insertion is found, using the (keys(left) < key(root) < keys(right) property of the BST) 

2. While we are traversing down the tree to find and insert our new node, at every node we recurse to (these are the ancestor nodes of the node we are currently inserting), 


