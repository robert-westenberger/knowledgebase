---
title: Backtracking
description: 
published: true
date: 2022-05-12T16:02:45.266Z
tags: algorithms, backtracking
editor: markdown
---

# Overview
Backtracking is a technique for solving problems by exploring all possible solutions.

It is a systematic way to run through all the possible configurations of a search search. These configurations may represent all possible arrangements of objects (permutations) or all possible ways of building a collection of them (subsets). 

## Generic Backtracking
1. Start from a state
2. If the current state is a solution, add the current state to the result. 
3. If not, try each of the possible moves from the current state.
4. Once we have tried all the possible moves, backtrack to the previous state.
5. Repeat the above steps until a solution is found or all possibilities have been exhausted.