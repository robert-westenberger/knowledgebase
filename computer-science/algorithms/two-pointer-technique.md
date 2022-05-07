---
title: Two Pointer Technique
description: 
published: true
date: 2022-05-07T22:34:41.977Z
tags: algorithms, pointers
editor: markdown
---

# Overview
Typically used for searching pairs in a sorted array. 

## Example
Given a sorted array $A$ (in ascending order), having $N$ integers, find if there exists any pair of elements $(A[i], A[j])$ such that their sum is equal to $X$.

We start the sum of extreme values (smallest and largest) and conditionally move both pointers. 

We move left pointer to the right when the sum of $(A[i]$ and $(A[j])$ is less than $X$. 

We move the right pointer to the left when the sum of $(A[i]$ and $(A[j])$ is greater than $X$.