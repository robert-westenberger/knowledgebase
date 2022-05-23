---
title: Populating Next Right Pointers in Each Node
description: 
published: true
date: 2022-05-23T18:24:22.066Z
tags: algorithms, trees, binary-trees
editor: markdown
---

# Problem
You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:
```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.
## Examples
![populating-next-right-tree-node.png](/populating-next-right-tree-node.png)


# Approach
Save a pointer to head.

1. While root and root.left exist..
  a. Set a pointer NEXT to the root's left node. 
  b. While root exists
    i. Set the root's left next node to root's right node.
    ii. Set the root's right next node to root.next.left if it exist's, null otherwise.
    ii. Set root to root.next (Traversing the tree).
  c. Set root to next (traversing the tree)
2. Return head.
## Implementation(Javascript)
```
const connect = function(root) {
    const head = root;
    while (root && root.left) {
        const next = root.left;
        while (root) {
            root.left.next = root.right;
            root.right.next = root.next ? root.next.left : null;
            root = root.next;
        }
        root = next;
    }
    return head;
}
```