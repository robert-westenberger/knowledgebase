---
title: Range Sum of BST
description: 
published: true
date: 2022-05-03T14:47:02.517Z
tags: algorithms, trees, binary-trees, binary-search-trees
editor: markdown
---

# Problem
Given the root node of a binary search tree and two integers low and high, return the sum of values of all nodes with a value in the inclusive range [low, high].

## Constraints
- The number of nodes in the tree is in the range [1, 2 * 10^4^].
- 1 <= Node.val <= 10^5^
- 1 <= low <= high <= 10^5^
- All Node.val are unique.

## Examples
**Input**
<pre>
   10
   /\
  5 15
 /\   \
 3 7  18
</pre>
low=7 high=15
**Output**: 32
**Explanation**: Nodes 7, 10, and 15 are in the range [7, 15]. 7 + 10 + 15 = 32.