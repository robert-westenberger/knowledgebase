---
title: Maximum Binary Tree
description: 
published: true
date: 2022-05-03T16:01:41.992Z
tags: algorithms, trees, binary-trees
editor: markdown
---

# Problem
You are given an integer array nums with no duplicates. A maximum binary tree can be built recursively from nums using the following algorithm:

1. Create a root node whose value is the maximum value in nums.
2. Recursively build the left subtree on the subarray prefix to the left of the maximum value.
3. Recursively build the right subtree on the subarray suffix to the right of the maximum value.

Return the maximum binary tree built from nums.

## Constraints
1 <= nums.length <= 1000
0 <= nums[i] <= 1000
All integers in nums are unique.

## Examples
Input: nums = [3, 2, 1, 6, 0, 5]
Output:
<pre>
   6
 /  \
 3   5
 \   /
  2 0
   \
    1

</pre>

# Approach
Starting from the root, which is the max value in the array, we recurse down left and right subtrees. 
## Implementation (Javascript)
const constructMaximumBinaryTree = function(nums) {
    if (!nums.length) {
        return null;
    }

    const max = Math.max(...nums);
    const index = nums.indexOf(max); 
    const root = new TreeNode(max);
 
    root.left = constructMaximumBinaryTree(nums.slice(0, index));
    root.right = constructMaximumBinaryTree(nums.slice(index+1, nums.length));

    return root;
};