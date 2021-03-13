---
title: Proofs Involving Sets
description: 
published: true
date: 2021-03-13T21:07:00.141Z
tags: mathematics, discrete-mathematics
editor: markdown
---

## How to Prove $a \in A$

* To show $\mathbf{a} \in\{\mathbf{x}: \mathbf{P}(\mathbf{x})\}$ 	
	* show that $P(a)$ is true.

* To show $\mathbf{a} \in\{\mathbf{x} \in \mathbf{S}: \mathbf{P}(\mathbf{x})\}$
	* Verify that $a \in S$
  * Show that $P(a)$ is true.
  
  
## Examples
$A=\{x: x \in \mathbb{N}$ and $7 \mid x\}$
This set has form $A = \{x:P(x)\}$ where $P(x)$ is the open sentence $(x \in \mathbb{N}) \wedge(7 \mid x)$. Thus $21 \in A$ because $P(21)$ is true. Similarly, $7, 14, 28, 35$ etc are all elements of $A$. But $8 \notin A$ for example because $P(8)$ is false. Likewise, $-14 \notin A$ because $P(-14)$ is false. 