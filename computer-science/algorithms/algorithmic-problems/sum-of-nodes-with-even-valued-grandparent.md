---
title: Sum of Nodes With Even Valued Grandparent
description: 
published: true
date: 2022-05-03T14:42:08.394Z
tags: algorithms, trees, binary-trees
editor: markdown
---

# Problem
Given the root of a binary tree, return the sum of values of nodes with an even-valued grandparent. If there are no nodes with an even-valued grandparent, return 0.

A grandparent of a node is the parent of its parent if it exists.

## Constraints
- The number of nodes in the tree is in the range [1, 10^4^].
- 1 <= Node.val <= 100

# Approach
For each node that is not null, check if they have grandparent. If their grandparent is even valued, add the node's data to the sum. 

## Implementation (Javascript)
```
const sumEvenGrandparent = function(root) {
    let answer = 0;
    const getSum = (current, parent, grandparent) => {
        if (current == null) {
            return 0;
        }
        if (grandparent != null && grandparent.val % 2 === 0) {
            answer += current.val;
        }

        getSum(current.left, current, parent);
        getSum(current.right, current, parent);
    }
    getSum(root, null, null);
    return answer;
};
```