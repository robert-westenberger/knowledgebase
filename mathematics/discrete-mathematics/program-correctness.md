---
title: Program Correctness
description: 
published: true
date: 2021-07-08T18:21:07.263Z
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