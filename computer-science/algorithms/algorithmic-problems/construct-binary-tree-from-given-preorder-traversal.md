---
title: Construct  Binary Search Tree From Given Preorder Traversal
description: 
published: true
date: 2022-05-05T17:37:17.525Z
tags: algorithms, binary-trees, binary-search-trees
editor: markdown
---

# Header
Your content here

## WIP
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {number[]} preorder
 * @return {TreeNode}
 */

const bstFromPreorder = function(preorder) {
    // console.log(preorder);
    const root = new TreeNode(preorder.shift());
    const nodeQueue = [root];
    let rightSubtreeIndex = preorder.length - 1;
    // find index of first item in right subtree
    for (let i = preorder.length; i > 0; i--) {
        const item = preorder[i];
        if (item < root.val) {
            break;
        }
        if (item < preorder[rightSubtreeIndex]) {
            rightSubtreeIndex = i;
        }
    }
    const leftTreeVals = preorder.slice(0, rightSubtreeIndex);
    const rightTreeVals = preorder.slice(rightSubtreeIndex, preorder.length);
    
    root,.
    
};