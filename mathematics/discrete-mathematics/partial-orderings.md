---
title: Partial Orderings
description: 
published: true
date: 2021-06-09T17:13:42.188Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Partial Orderings

A relation $R$ on a set $S$ is called a partial ordering or partial order if it is **reflexive**, **antisymmetric**, and **transitive**. A set $S$ together with a partial ordering $R$ is called a partially ordered set, or poset, and is denoted by $(S, R)$. Members of $S$ are called elements of the poset.

## Antisymmetry
Let $R$ be a relation on a set $A . R$ is antisymmetric if, and only if, for every $a$ and $b$ in $A,$ if $a R b$ and $b R a$ then $a=b$.

In terms of an arrow diagram of a relation, saying that a relation is antisymmetric is the same as saying that whenever there is an arrow goign from one element to another distinct element, there is not an arrow going back from the second to the first.

### Example: Testing for Antisymmetry of "Divides" Relations
Let $R_1$ be the "divides" relation on the set of all positive integers, and $R_2$ be the "divides" relation on the set of all integers. Prove or give a counterexample of $R_1$ and $R_2$ being antisymmetric.

$R_1$ is antisymmetric. 
**Proof:** Suppose $a$ and $b$ are positive integers such that $a R_{1} b$ and $b R_{1} a$. [We must show that $a=b .]$ By definition of $R_{1}, a \mid b$ and $b \mid a$. Thus, by definition of divides, there are integers $k_{1}$ and $k_{2}$ with $b=k_{1} a$ and $a=k_{2} b$. It follows that 
$$ 
b=k_{1} a=k_{1}\left(k_{2} b\right)=\left(k_{1} k_{2}\right) b .
$$
Dividing both sides by $b$ gives 
$$ k_{1} k_{2}=1 $$