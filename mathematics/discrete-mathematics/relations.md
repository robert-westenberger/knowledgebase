---
title: Relations
description: 
published: true
date: 2021-04-27T19:34:17.806Z
tags: discrete-mathematics
editor: markdown
---

# Binary Relations
A **binary relation**, $R$, consists of a set, $A$, called the **domain** of $R$, a set, $B$, called the **codomain** of $R$, and a subset of $A \times B$ called the **graph** of $R$. The graph of a function has the property that every element of $A$ is the first element of exactly one ordered pair of the graph.

A relation whose domain is $A$ and codomain is $B$ is said to be "between $A$ and $B$", or "from $A$ to $B$." 

When the domain and codomain are the same set, $A$, we simply say the relation is "on A." 

It is common to use "$a \medspace R \medspace b$" to mean the pair $(a, b)$ is in the graph of $R$.

Relationships between elements of more than two sets arise in many contexts. These relationships can be represented by $n$-ary relations, which are collections of $n$-tuples. Such relations are the basis of the relational data model, the most common way to store information in computer databases.

## Properties of Relations


### Reflexive


## Types Binary Relations
(Diagrams of two example functions)![diagrams_of_two_functions.png](/diagrams_of_two_functions.png)

(Left is total and surjective, but not injective)
(Right is total and injective but not surjective)
(If $f$ is a function, it means that every point in the domain column, $A$, has at most one arrow out of it. (If more than one arrow comes out of the first column, then it would be a relation not a function). 


We say a function $f: A \rightarrow B$ is:

### Total and Partial
**Total** if every element of $A$ is assigned to some element of $B$, otherwise $f$ is called a **partial** function.

"$f$ is total" means that every point in the domain column of a function graph has at least one arrow out of it, which really means it has exactly one arrow out of it since $f$ is a function. 
### Surjective
If every element of $B$ is mapped at least once. Also known as **onto**.
This is a property of the codomain.
For every element $b \in B$, there exists an element $a \in A$ such that
$$f(a) = b$$


"$f$ is surjective" means that evry point in the codomain column has at least one arrow into it.
If $A$ is a finite set, we let $|A|$ be the number of elements in $A$. If $f : A \rarr B$ is surjective, then $|A| \geq|B|$.
### Injective
If every element of $B$ is mapped to at most once. Also known as **one-to-one**. This is a property of the domain of a function. 

"$f$ is injective" means that every point in the codomain column, $B$, has at most one arrow into it. 

If $A$ is a finite set, we let $|A|$ be the number of elements in $A$. If $f : A \rarr B$ is total and injective, then $|A| \leq|B|$.

$$
f\left(x_{1}\right)=f\left(x_{2}\right) \Rightarrow x_{1}=x_{2}
$$
for all elements $x_{1}, x_{2} \in A$
### Bijective
If $f$ is total, surjective, and injective. In particular, each element of $B$ is mapped to exactly once.

"$f$ is bijective" means that every point in the $A$ column has exactly one arrow out of it, and every point in the $B$ column has exactly one arrow into it.
If $A$ is a finite set, we let $|A|$ be the number of elements in $A$. If $f : A \rarr B$ is bijective, then $|A| =|B|$.

## Increasing and Decreasing
A function $f$ whose domain and codomain are subsets of the set of real numbers is **increasing** if $f(x) \leq f(y)$ and **strictly increasing** if $f(x) \lt f(y)$, wherever $x \lt y$ and $x$ and $y$ are in the domain of $f$. $f$ is **decreasing** if $f(x) \geq f(y)$ and **stricly decreasing** if $f(x) \gt f(y)$


## Relational Images