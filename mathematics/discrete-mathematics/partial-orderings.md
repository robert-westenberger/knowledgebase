---
title: Partial Orderings
description: 
published: true
date: 2021-06-10T18:00:20.436Z
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

Now since $a$ and $b$ are both integers, $k_{1}$ and $k_{2}$ are both positive integers also. And the only product of two positive integers that equals 1 is $1 \cdot 1$. Thus 
$$ k_{1}=k_{2}=1 $$ 
and so 
$$ a=k_{2} b=1 \cdot b=b $$
[as was to be shown].

$R_2$ is not antisymmetric. Let $a=2$ and $b=-2$. Then $a \mid b$ since $-2=(-1) \cdot 2]$ and $b \mid a$ [since $2=(-1)(-2)]$. Hence $a R_{2} b$ and $b R_{2} a$ but $a \neq b$.

### Example: Show that the greater than or equal to relation is a partial ordering on the set of integers
Because $a \geq a$ for every integer $a, \geq$ is reflexive. If $a \geq b$ and $b \geq a$, then $a=b$. Hence, $\geq$ is antisymmetric. Finally, $\geq$ is transitive because $a \geq b$ and $b \geq c$ imply that $a \geq c$. It follows that $\geq$ is a partial ordering on the set of integers and $(\mathbf{Z}, \geq)$ is a poset.

### Example: Show that the inclusion relation $\subseteq$ is a partial ordering on the power set of a set $S$.
Because $A \subseteq A$ whenever $A$ is a subset of $S \subseteq$ is reflexive. It is antisymmetric because $A \subseteq \mid B$ and $B \subseteq A$ imply that $A=B$. Finally, $\subseteq$ is transitive, because $A \subseteq B$ and $B \subseteq C$ imply that $A \subseteq C$. Hence, $\subseteq$ is a partial ordering on $P(S)$, and $(P(S) \subseteq)$ is a poset.

## Comparability and Totally Ordered sets
Suppose $\preceq$ is a partial order relation on a set $A$. Elements $a$ and $b$ of $A$ are said to be **comparable** if, and only if, either $a \preceq b$ or $b \preceq a$. Otherwise, $a$ and $b$ are called **noncomparable**.

Given any two real numbers $x$ and $y$, either $x \leq y$ or $y \leq x$. The elements  $x$ and $y$ in this case are **comparable**.

Given two subsets $A$ and $B$ of $\{a,b,c\}$, it may be the case that neither $A \subseteq B$ nor $B \subseteq A$. For instance, let $A=\{a, b\}$ and $B=\{b, c\} .$ Then $A \nsubseteq B$ and $B \nsubseteq A .$ In such a case, $A$ and $B$ are said to be **noncomparable**.

When every two elements in the set are comparable, the relation is called a **total ordering**.

If $(S, \preccurlyeq)$ is a poset and every two elements of $S$ are comparable, $S$ is called a **totally ordered** or **linearly ordered** set, and $\preccurlyeq$ is called a total order or a linear order. A totally ordered set is also called a **chain**.
