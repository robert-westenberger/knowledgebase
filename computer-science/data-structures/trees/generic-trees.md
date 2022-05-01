---
title: Generic / N-array Trees
description: 
published: true
date: 2022-05-01T23:39:15.957Z
tags: data-structures, trees
editor: markdown
---

# Overview

N-ary trees are tree data structures that allow us to have up to n children nodes for each of the nodes, differing from the standard binary trees which allow only up to 2 children nodes for each node.

## Implementation
```
class TreeNode {
    int val;
    TreeNode[] children;
}
```