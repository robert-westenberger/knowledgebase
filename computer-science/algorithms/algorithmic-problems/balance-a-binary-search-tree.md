---
title: Balance a Binary Search Tree
description: 
published: true
date: 2022-05-03T16:20:14.874Z
tags: algorithms, trees, binary-search-trees
editor: markdown
---

# Problem
Given the root of a binary search tree, return a balanced binary search tree with the same node values. If there is more than one answer, return any of them.

A binary search tree is balanced if the depth of the two subtrees of every node never differs by more than 1.

## Constraints
- The number of nodes in the tree is in the range [1, 10^4^].
- 1 <= Node.val <= 105

# Approach

## Implementation (Javascript)
```
const storeNodes = (root, nodes) => {
    if (root == null) {
        return null;
    }
    storeNodes(root.left, nodes);
    nodes.push(root.val);
    storeNodes(root.right, nodes);
}

const balanceBSTUtil = (nodes, start, end) => {
    if (start > end) {
        return null;
    }
    const mid = Math.floor((start + end) / 2);
    const node = new TreeNode(nodes[mid]);
    node.left = balanceBSTUtil(nodes, start, mid - 1);
    node.right = balanceBSTUtil(nodes, mid+1, end);
    return node;
}
const balanceBST = function(root) {
    const nodes = [];
    storeNodes(root, nodes);
    return balanceBSTUtil(nodes, 0, nodes.length - 1);
};
```