---
title: Maximum Difference Between Node and Ancestor
description: 
published: true
date: 2022-05-10T16:29:59.964Z
tags: algorithms, trees, recursion, binary-trees
editor: markdown
---

# Problem
Given the root of a binary tree, find the maximum value v for which there exist different nodes a and b where v = |a.val - b.val| and a is an ancestor of b.

A node a is an ancestor of b if either: any child of a is equal to b or any child of a is an ancestor of b.

## Approach
At each subtree, find the minimum and maximum value. We store these in memory at every level of recursion. 

When we recurse, we check the difference between the current node's value and the minimum and maximum value of the subtree. If it is larger than the current maximum difference found, we made that the new largest difference found. 