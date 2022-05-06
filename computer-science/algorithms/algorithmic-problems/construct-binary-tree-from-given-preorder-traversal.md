---
title: Construct  Binary Search Tree From Given Preorder Traversal
description: 
published: true
date: 2022-05-06T16:35:03.593Z
tags: algorithms, binary-trees, binary-search-trees
editor: markdown
---

# Problem
Given an array of integers preorder, which represents the preorder traversal of a BST (i.e., binary search tree), construct the tree and return its root.

It is guaranteed that there is always possible to find a binary search tree with the given requirements for the given test cases.

A binary search tree is a binary tree where for every node, any descendant of Node.left has a value strictly less than Node.val, and any descendant of Node.right has a value strictly greater than Node.val.

A preorder traversal of a binary tree displays the value of the node first, then traverses Node.left, then traverses Node.right.

# Approach
## Implementation (Javascript)
```
const constructBST = (preorder, size, position, current, left, right, level) => {

    if (position === size || preorder[position] < left || preorder[position] > right) {
        return position;
    }
    
    if (preorder[position] < current.val) {
        current.left = new TreeNode(preorder[position]);
        position += 1;
        position = constructBST(preorder, size, position, current.left, left, current.val - 1);
    }
    
    if (position === size || preorder[position] < left || preorder[position]>right){
        return position;
    }
    
    current.right = new TreeNode(preorder[position]);
    position+= 1;
    position = constructBST(preorder, size, position, current.right, current.val + 1, right);
    return position;
}
const bstFromPreorder = function(preorder) {
    const size = preorder.length;
    if (size === 0) {
        return null;
    }
    const root = new TreeNode(preorder[0]);
    if (size === 1) {
        return root;
    }
    constructBST(preorder, size, 1, root, Number.MIN_SAFE_INTEGER, Number.MAX_SAFE_INTEGER);
    return root;
};
```
### Example 
With a preorder of [8, 5, 1, 7, 10, 12]

