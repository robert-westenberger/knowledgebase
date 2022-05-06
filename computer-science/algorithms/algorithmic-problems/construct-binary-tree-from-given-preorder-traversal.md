---
title: Construct  Binary Search Tree From Given Preorder Traversal
description: 
published: true
date: 2022-05-06T15:32:47.249Z
tags: algorithms, binary-trees, binary-search-trees
editor: markdown
---

# Problem
Given an array of integers preorder, which represents the preorder traversal of a BST (i.e., binary search tree), construct the tree and return its root.

It is guaranteed that there is always possible to find a binary search tree with the given requirements for the given test cases.

A binary search tree is a binary tree where for every node, any descendant of Node.left has a value strictly less than Node.val, and any descendant of Node.right has a value strictly greater than Node.val.

A preorder traversal of a binary tree displays the value of the node first, then traverses Node.left, then traverses Node.right.

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