---
title: Maximum Difference Between Node and Ancestor
description: 
published: true
date: 2022-05-10T16:30:19.050Z
tags: algorithms, trees, recursion, binary-trees
editor: markdown
---

# Problem
Given the root of a binary tree, find the maximum value v for which there exist different nodes a and b where v = |a.val - b.val| and a is an ancestor of b.

A node a is an ancestor of b if either: any child of a is equal to b or any child of a is an ancestor of b.

## Approach
At each subtree, find the minimum and maximum value. We store these in memory at every level of recursion. 

When we recurse, we check the difference between the current node's value and the minimum and maximum value of the subtree. If it is larger than the current maximum difference found, we made that the new largest difference found. 

### Implementation (Javascript)
function Result() {
    this.r = 0;
}
const maxAncestorDiff = function(root) {
    if (root == null) {
        return 0;
    }
    const answer = new Result();
    const traverse = (node, min, max) => {
       if (node == null) {
           return 0;
       }
       answer.r = Math.max(answer.r, Math.abs(node.val - min), Math.abs(node.val - max));
       min = Math.min(min, node.val);
       max = Math.max(max, node.val);
       traverse(node.left, min, max);
       traverse(node.right, min, max);
    }

    
    traverse(root, root.val, root.val);
    return answer.r;
};