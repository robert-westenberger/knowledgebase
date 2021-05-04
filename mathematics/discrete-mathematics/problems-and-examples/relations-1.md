---
title: Relations 1 Exercises
description: 
published: true
date: 2021-05-04T18:06:39.650Z
tags: discrete-mathematics
editor: markdown
---

# Determine if relations on a set are reflexive, symmetric, antisymmetric, or transitive

## Rosen 7th Edition Sec 9.1 Exercise 3
For each of these relations on the set $\{1,2,3,4\}$, decide
whether it is reflexive, whether it is symmetric, whether
it is antisymmetric, and whether it is transitive.
**a)** $\{(2,2),(2,3),(2,4),(3,2),(3,3),(3,4)\}$
**b)** $\{(1,1),(1,2),(2,1),(2,2),(3,3),(4,4)\}$
**c)** $\{(2,4),(4,2)\}$
**d)** $\{(1,2),(2,3),(3,4)\}$
**e)** $\{(1,1),(2,2),(3,3),(4,4)\}$
**f)** $\{(1,3),(1,4),(2,3),(2,4),(3,1),(3,4)\}$.

### Soln
**a)** Transitive.
**b)** This is reflexive since it contains $(a, a) \in R$ for every $a \in A$. It is also symmetric since $(2,1)$ is in $R$ when $(1, 2)$ is. It is not antisymmetric since $(1,2)$ and $(2,1)$ are in the relation. It is transitive since $(1,2)$ and $(2, 1)$ are in the relation then $(1,1)$ and $(2,2)$ are in the relation as well.
**c)** Not reflexive, but it is symmetric. Not antisymmetric because $(2,4)$ and $(4,2)$ are in the relation. IT isn't transitive because $(2,4)$ and $(4,2)$ are in the relation but $(2,2)$ is not.
**d)** Not reflexive or symmetrical. It is antisymmetric since there are no cases of $(a,b)$ being in the relation when $(b, a)$ is. It is not transitive since although $(1,2)$ and $(2,3)$ are in the relation, $(1,3)$ is not.
**e)** Reflexive, symmetric, antisymmetric, and transitive (the only tyime the hypothesis ($(a, b) \in R \wedge(b, c) \in R$) is met is when $a=b=c$.
**f)** Not reflexive or symmetric or antisymmetric. It is not transitive, since $(2,3)$ and $(3,1)$ are in the relation, but $(2,1)$ is not.

## Rosen 7th Edition Sec 9.1 Exercise 5
Determine whether the relation $R$ on the set of all Web pages is reflexive, symmetric, antisymmetric, and/or transitive, where $(a, b) \in R$ if and only if

**a)** everyone who has visited Web page $a$ has also visitedWeb page $b$.
**b)** there are no common links found on both Webpage $a$ and Web page $b$.
**c)** there is at least one common link onWeb page $a$ andWeb page $b$.
**d)** there is a Web page that includes links to both Webpage $a$ and Web page $b$.

### Soln
**a)** It's reflexive (if you visited website $a$ you have also visited website $a$..) It is not symmetric since there must exist a website $a$ and $b$ such that the set of people who visited $a$ are a proper subset of $b$. If there exists two different web pages that have the same exact set of visitors, then $R$ is not antisymmetric. $R$ is transitive (if everyone who visited $a$ visited $b$, and everyone who visited $b$ visited $c$, then everyone who visited $a$ has also visited $c$.
**b)** Not reflexive, any page $a$ that has links on it, $(a, a) \notin R$. $R$ is symmetric in its very definition. $R$ is not antisymmetric because there are surely two different webpages $a$ and $b$ that have no common links in them. Lastly, $R$ is not transitive since for webpages with no links in common, if they have links at all, give an example of a failure of the definition $(a, b) \in R$ and $(b,a) \in R$, but $(a, a) \notin R$.
**c)**
**d)**
# Determine whether a relation is an equivalence relation ( reflexive, symmetric, and transitive)
## 2000 Solved Problems in Discrete Mathematics 2.180
Let $R$ be the relation ont he set $N$ of positive integers defined by $R=\{(a,b): a + b \medspace \text {is even}\}$. Is $R$ an equivalence relation?
### Soln
It is reflexive ($a+a$ is even).
It is symmetric (if $a+b$ is even then $b+a$ is even).
It is transitive (if $a+b$ is even and $b+c$ is even then $a+c$ is also even)

It is reflexive, symmetric, and transitive, so it is an equivalence relation.
## 2000 Solved Problems in Discrete Mathematics 2.181
Let $S$ be the relation "is a blood relative of" on the set $X$ of people. Is $S$ an equivalence relation?

It is not reflexive (a person can't be a blood relative of themselves, that doesnt make sense. The book says this is reflexive, so they are considering a person a relative of themselves...). 
It is symmetric (if a person $a$ has a blood relative $b$, then person $b$ is a blood relative of $a$).
It is not transitive (a person may have a cousin $a$ through his mothers family and another cousin $b$ through their fathers family, but $a$ and $c$ may not be blood relatives).
## 2000 Solved Problems in Discrete Mathematics 2.182 
Let $R = \{(1,1),(1,3),(3,1),(3,3)\}$. Is $R$ an equivalence relation on $A=\{1,2,3\}$? on $B=\{1,3\}$?
### Solution
For $A$, its not reflexive since its missing $(2,2)$, so its not an equivalence relation.
For $B$, it is symmetric, reflexive, and transitive so it is an equivalence relation.

## MIT OCW 6.042J Fall 2005 In-Class Problems Week 4 Problem 1
In each case, say whether or not $R$ is an equivalence relation on $A$. If it is an equivalence relation, what are the equivalence classes and how many equivalence clases are there?

### Solution

# Show that a relation is an equivalence relation ( reflexive, symmetric, and transitive)
## Rosen 7th Edition Sec 9.1 Exercise 9
Show that the relation $R=\emptyset$ on the empty set $S=\emptyset$ is reflexive, symmetric, and transitive.
### Soln
Each of the properties reflexive, symmetric, and transitive are universally quantified statements. Because the domain is empty, each of them is vacuously true.
**a)** $R::=\{(x, y) \in W \times W \mid$ the words $x$ and $y$ start with the same letter $\}$ where $W$ is the set of all words in the 2001 edition of the Oxford English dictionary.
**b)** $R::=\{(x, y) \in W \times W \mid$ the words $x$ and $y$ have at least one letter in common $\}$
**c)** $R=\{(x, y) \in W \times W$ and the word $x$ comes before the word $y$ alphabetically $\}$
**d)** $R=\{(x, y) \in \mathbb{R} \times \mathbb{R}$ and $|x| \leq|y|\}$
**e)** $R=\{(x, y) \in B \times B$, where $\mathrm{B} \medspace \text {is the set of all bit strings and} \medspace \mathrm{x} \medspace \text {and} \medspace \mathrm{y} \medspace \text { have the same number of 1s\} }$.
# Determine which relations are irreflexive
## Rosen 7th Edition Sec 9.1 Exercise 11
A relation $R$ on the set $A$ is irreflexive if for every $a \in A$, $(a, a) \notin R$. That is, $R$ is irreflexive if no element in $A$ is related to itself. 

Which relations from exercise 3 are irreflexive?
### Soln
c, d, f are irreflexive.

# Answer about the nature of reflexivity / irreflexivity
## Rosen 7th Edition Sec 9.1 Exercise 15
Can a relation on a set be neither reflexive nor irreflexive?

### Soln
Yes, a relation $R$ may contain some pairs of $(a, a)$ but not all of them.
## Rosen 7th Edition Sec 9.1 Exercise 17
Give an example of an irreflexive relation on the set of all people.
### Soln
$(a,b) \in R$ iff $a$ weighs more than $b$. A person can't weigh more than themselves, so this is irreflexive.

# Use quantifiers to express a statement about a relation
## Rosen 7th Edition Sec 9.1 Exercise 23
Use quantifiers to express what it means for a relation to be asymmetric.

### Soln
$$
\forall a \forall b \neg((a, b) \in R \wedge(b, a) \in R)
$$
or 
$$
\forall a \forall b((a, b) \in R \rightarrow(b, a) \notin R)
$$

