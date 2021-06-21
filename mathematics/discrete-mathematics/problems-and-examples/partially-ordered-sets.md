---
title: Partially Ordered Sets Exercises
description: 
published: true
date: 2021-06-21T17:33:49.366Z
tags: discrete-mathematics
editor: markdown
---

## Discrete Mathematics with Applications 5th Edition (Epp) Section 8.5 Exercise 38
Prove that a partially ordered set is totally ordered if, and only if, it is a chain.

### Solution
Suppose $A$ is a partially ordered set with respect to a relation $\preceq$. By definition of total order, $A$ is totally ordered if, and only if, any two elements of $A$ are comparable. By definition of chain, this is true if, and only if, $A$ is a chain.

## Discrete Mathematics with Applications 5th Edition (Epp) Section 8.5 Exercise 39
Suppose that $A$ is a totally ordered set. Use mathematical induction to prove that for any integer $n \geq 1$, every subset of $A$ with $n$ elements has both a least element and a greatest element.

### Solution
**Proof (by mathematical induction):** Let $A$ be a set that is totally ordered with respect to a relation $\preceq$, and let the property $P(n)$ be the sentence "Every subset of $A$ with $n$ elements has both a least element and a greatest element."

**Show that $P(1)$ is true:**
If $A=\varnothing$, then $P(1)$ is true by default. So assume that $A$ has at least one element, and suppose $S=\left\{a_{1}\right\}$ is a subset of $A$ with one element. Because $\preceq$ is reflexive, $a_{1} \preceq a_{1} .$ So, by definition of least element and greatest element, $a_{1}$ is both a least element and a greatest element of $S$, and thus the property is true for $n=1$. 

**Show that for every integer** **$k \geq 1$, if $P(k)$ is true, then $P(k+1)$ is true:**

Let $k$ be any integer with $k \geq 1$, and suppose that any subset of $A$ with $k$ elements has both a least element and a greatest element. [Inductive hypothesis.] We must show that any subset of $A$ with $k+1$ elements has both a least element and a greatest element. If $A$ has fewer than $k+1$ elements, then the statement is true by default. So assume that $A$ has at least $k+1$ elements and that $S=\left\{a_{1}, a_{2}, \ldots, a_{k+1}\right\}$ is a subset of $A$ with $k+1$ elements. By inductive hypothesis, $S-\left\{a_{k+1}\right\}$ has both a least element $s$ and a greatest element $t$. Now because $A$ is totally ordered, $a_{k+1}$ and $s$ are comparable. If $a_{k+1} \preceq s$, then, by transitivity of $\preceq, a_{k+1}$ is the least element of $S$; otherwise, $s$ remains the least element of $S$. And if $t \preceq a_{k+1}$, then, by transitivity of $\preceq, a_{k+1}$ is the greatest element of $S$; otherwise, $t$ remains the greatest element of $S$. Thus $S$ has both a greatest element and a least element [as was to be shown].