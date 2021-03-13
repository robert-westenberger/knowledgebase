---
title: Proofs Involving Sets
description: 
published: true
date: 2021-03-13T22:41:44.265Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# How to Prove $a \in A$

* To show $\mathbf{a} \in\{\mathbf{x}: \mathbf{P}(\mathbf{x})\}$ 	
	* show that $P(a)$ is true.

* To show $\mathbf{a} \in\{\mathbf{x} \in \mathbf{S}: \mathbf{P}(\mathbf{x})\}$
	* Verify that $a \in S$
  * Show that $P(a)$ is true.
  
  
## Examples
### Example 1
$A=\{x: x \in \mathbb{N}$ and $7 \mid x\}$
This set has form $A = \{x:P(x)\}$ where $P(x)$ is the open sentence $(x \in \mathbb{N}) \wedge(7 \mid x)$. Thus $21 \in A$ because $P(21)$ is true. Similarly, $7, 14, 28, 35$ etc are all elements of $A$. But $8 \notin A$ for example because $P(8)$ is false. Likewise, $-14 \notin A$ because $P(-14)$ is false. 

### Example 2
$A=\{X \in \mathscr{P}(\mathbb{N}):|X|=3\}$
We know that $\{4,13,45\}\in A$ because $\{4,13,45\} \in \mathscr{P}(\mathbb{N})$ and $|\{4,13,45\}|=3$.
However, $\{1,2,3,4\} \notin A$ because $|\{1,2,3,4\}| \neq 3$

### Example 3
$B=\{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod \medspace 5)\}$

$(8,23)\in B$ because $(8,23) \in \mathbb{Z} \times \mathbb{Z}$ and $8 \equiv 23(\bmod \medspace 5)$.
Likewise, $(100, 75) \in B$, $(102, 77) \in B$ etc., but $(6, 10) \notin B$

Suppose $n \in \mathbb{Z}$ and consider the ordered pair $(4 n+3,9 n-2)$. Does this ordered pair belong in $B$? To answer this, we observe that $(4 n+3,9 n-2) \in \mathbb{Z} \times \mathbb{Z}$. Next, we observe $(4 n+3)-(9 n-2)=-5 n+5=5(1-n)$, so $5 \mid((4 n+3)-(9 n-2))$, which means $(4 n+3) \equiv(9 n-2)(\bmod 5)$. Therefore we have established that $(4 n+3,9 n-2)$ meets the requirements for belonging to $B$, so $(4 n+3,9 n-2) \in B$ for every $n \in \mathbb{Z}$.

### Example 4
$C=\left\{3 x^{3}+2: x \in \mathbb{Z}\right\}$

Elements of this set consist of all the values $3x^3 + 2$ where $x$ is an integer. Thus $-22 \in C$ because $-22=3(-2)^{3}+2$. You can confirm $-1 \in C$ and $5 \in C$. $0 \notin C$ and $\frac 12 \notin C$ etc.

# How to Prove $A \subseteq B$
To prove $A \subseteq B$, we need to prove
$$a \in A \longrightarrow a \in B$$
This can be proved directly, assuming $a \in A$ and deducing $a \in B$.

The contrapositive approach is another option: Assume $a \notin B$ and deduce $a \notin A$.

## Examples
### Example 1
Prove that $\{x \in \mathbb{Z}: 18 \mid x\} \subseteq\{x \in \mathbb{Z}: 6 \mid x\}$
(Prove the set of integers that are divisible by 18 is a subset of the set of integers that are divisible by 6) 
**Proof:**
1. Suppose  $a \in\{x \in \mathbb{Z}: 18 \mid x\}$.
	(Our supposition)
  
2. This means that $a \in \Z$ and $18 \vert a$.
