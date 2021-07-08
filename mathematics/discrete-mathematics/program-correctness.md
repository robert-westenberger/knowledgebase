---
title: Program Correctness
description: 
published: true
date: 2021-07-08T18:22:23.735Z
tags: computer-science, discrete-mathematics, algorithms
editor: markdown
---

# Program Verification
A proof that a program is **correct** (always produces the correct output for every possible input) consists of two parts:
1) Show that the correct answer is obtained if the program terminates. This part of the proof establishes the **partial correctness** of the program. 
2) Show that the program always terminates. 

## Specifying Correct Program Output
Two propositions are used to specify a program produces the correct output:
1) **Initial Assertion** - Gives properties that the input values must have.
2) **Final Assertion** - Gives the properties that the output of the program should have, if the program did what was intended. 

The appropriate and final assertions must be provided when a program is checked.

A program, or program segment, $S$ is said to be **partially correct with respect to** the initial assertion $p$ and the final assertion $q$ if whenever $p$ is true for the input values of $S$ and $S$ terminates, then $q$ is true for the output values of $S$. The notation $p\{S\} q$ indicates that the program, or program segment, $S$ is partially correct with respect to the initial assertion $p$ and the final assertion $q$.