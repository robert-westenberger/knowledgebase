---
title: Sets Exercises
description: 
published: true
date: 2021-04-12T00:48:34.107Z
tags: discrete-mathematics
editor: markdown
---

# Rosen Discrete Mathematics 7th Edition Section 2.1
## List members of sets

### 1 
List the members of these sets.
**a)** $\left\{x \mid x\right.$ is a real number such that $\left.x^{2}=1\right\}$
**b)** $\{x \mid x$ is a positive integer less than 12$\}$
**c)** $\{x \mid x$ is the square of an integer and $x<100\}$
**d)** $\left\{x \mid x\right.$ is an integer such that $\left.x^{2}=2\right\}$

#### Solution

**a)** $\{-1, 1 \}$
**b)** $\{0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12 \}$
**c)** $\{0, 1, 4, 9, 16, 25, 36, 49, 64, 81 \}$
**d)** $\emptyset$

### 3 
For each of these pairs of sets, determine whether the first
is a subset of the second, the second is a subset of the first,
or neither is a subset of the other.
**a)** the set of airline flights from New York to New Delhi,
the set of nonstop airline flights from New York to
New Delhi
**b)** the set of people who speak English, the set of people
who speak Chinese
**c)** the set of flying squirrels, the set of living creatures
that can fly
#### Solution
**a)** Every element in the second set is in the first set, so the second set is a subset of the first set. (the set of airline flights from new york to new delhi contains all nonstop flights + flights with layovers). 
**b)** neither
**c)** the first is a subset of the second, and not vice versa.

### 5
Determine whether each of these pairs of sets are equal.
**a)** $\{1,3,3,3,5,5,5,5,5\},\{5,3,1\}$
**b)** $\{\{1\}\},\{1,\{1\}\}$
**c)** $\emptyset,\{\emptyset\}$.
#### Solution
**a)** equal (duplicates and order dont matter)
**b)** not equal - first set has 1 element second has 2
**c)** not equal

### 21
Find the power set of each of these sets, where $a$ and $b$
are distinct elements.

**a)** $\{a\}$ 
**b)** $\{a, b\}$ 
**c)** $\{\emptyset,\{\emptyset\}\}$

#### Solution
**a)** $\{\{a\}, \emptyset\}$
**b)** $\{\emptyset,\{a\},\{b\},\{a, b\}\}$
**c)** $\{\emptyset,\{\emptyset\},\{\{\emptyset\}\},\{\emptyset,\{\emptyset\}\}\}$

### 25
Prove that $\mathcal{P}(A) \subseteq \mathcal{P}(B)$ if and only if $A \subseteq B$

#### Solution
We are proving an IFF so we have to show that $p \rarr q$ and $q \rarr p$.
We must prove $(\mathcal{P}(A) \subseteq \mathcal{P}(B) \rarr A \subseteq B) \wedge (A \subseteq B \rarr \mathcal{P}(A) \subseteq \mathcal{P}(B))$.

To prove that one set is a subset of another, we need to prove that an element being a member of one set implies membership of another set. 


**First Part: Prove** $(\mathcal{P}(A) \subseteq \mathcal{P}(B) \rarr A \subseteq B)$

Assume $\mathcal{P}(A) \subseteq \mathcal{P}(B)$. That is, $a \in \mathcal P(A)$ implies $a \in \mathcal P(B)$. 