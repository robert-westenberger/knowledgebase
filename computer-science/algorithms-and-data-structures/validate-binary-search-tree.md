---
title: Validate a Binary Search Tree
description: 
published: true
date: 2021-11-01T02:31:52.708Z
tags: algorithms
editor: markdown
---

# Definition of BST

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.

# Algorithm
Initialize two values, min and max, to the smallest and largest long values, respectively.

Then, starting from the root of the tree, do an inorder traversal. 

If the current node is NULL, return true. 

If the current node is either greater than max or less than min, return false. 

Otherwise, continue the inorder traversal, updating the max value when traversing left subchildren, and updating the min value when traversing right children. 
# C implementation
```
struct TreeNode
{
  int val;
  struct TreeNode *left;
  struct TreeNode *right;
};

bool isValidBSTHelper(struct TreeNode *root, long min, long max ) {
  if (!root) {
    return true;
  }
    
  if (root->val <= min || root->val >= max) {
    return false;
  }
  return isValidBSTHelper(root->left, min, root->val) && isValidBSTHelper(root->right, root->val, max);
}
bool isValidBST(struct TreeNode *root) {
  return isValidBSTHelper(root, LONG_MIN, LONG_MAX);
}

```