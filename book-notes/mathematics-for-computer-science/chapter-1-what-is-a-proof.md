---
title: Chapter 1: What is a Proof?
description: 
published: true
date: 2021-02-21T00:39:49.149Z
tags: computer-science, mathematics, book-notes, discrete-mathematics
editor: markdown
---

# What is a Proof? 
A **mathematical proof** of a **proposition** is a chain of **logical deductions** leading to the proposition from a base set of **axioms**. 

A **proposition** is a statement that is either true or false. 

**Claim:** For every nonnegative integer n the value of $n^2+n+41$ is prime.

We can check $n=0$ to $n=39$ and the claim holds true. However, for $n=40$ we get $40^2 + 40 + 41 = 41* 41$ which is not prime. This example highlights, in general, you can't check a claim about an infinite set by checking a finite sample of its elements, no matter how large the sample. 

There is a special notation for propositions about all numbers or all items of a certain kind: 

$$\forall n \in \natnums .p(n) \text{is prime.}$$