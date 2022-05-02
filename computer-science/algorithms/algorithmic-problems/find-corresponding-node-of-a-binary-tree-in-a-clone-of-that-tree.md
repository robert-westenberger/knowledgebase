---
title: Find a Corresponding Node of a Binary Tree in a Clone of that Tree
description: 
published: true
date: 2022-05-02T17:52:42.179Z
tags: algorithms, trees, binary-trees
editor: markdown
---

# Problem
Given two binary trees original and cloned and given a reference to a node target in the original tree.

The cloned tree is a copy of the original tree.

Return a reference to the same node in the cloned tree.

Note that you are not allowed to change any of the two trees or the target node and the answer must be a reference to a node in the cloned tree.

## Constraints 
The number of nodes in the tree is in the range [1, 10^4^].
The values of the nodes of the tree are unique.
target node is a node from the original tree and is not null.


# Approach
For this, we simultaneously recurse 
## Implementation (Javascript)
```
const getTargetCopy = function(original, cloned, target) { 
    if (original == null) {
        return original;
    }
    if (original.val === target.val) {
        return cloned;
    }
    
    const left = getTargetCopy(original.left, cloned.left, target);
    const right = getTargetCopy(original.right, cloned.right, target);
    return left != null ? left : right;
}
```