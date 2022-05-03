---
title: Range Sum of BST
description: 
published: true
date: 2022-05-03T15:01:40.045Z
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

# Approach
Traverse the tree recursively. If the value of the current node is in range, add it to the sum. If the current value is greater than the lower bound, continue traversing left. If the current value is less than the higher bound, continue traversing right. 

## Implementation (Javascript)
```
const rangeSumBST = function(root, low, high) {
    let answer = 0;
    const traverse = (node) => {
        if (node == null){
            return;
        }
        if (low <= node.val && node.val <= high) {
            answer += node.val;
        }
  
        if (node.val > low) {
            traverse(node.left);
        }
        if (node.val < high) {
            traverse(node.right);
        }
         
    }
    traverse(root);
    return answer;
};
```