---
title: Relations and Their Properties
description: 
published: true
date: 2021-06-22T18:05:45.550Z
tags: discrete-mathematics
editor: markdown
---

## Rosen 7th Edition Sec 9.1 Exercise 22
Must an asymmetric relation also be antisymmetric? Must an antisymmetric relation be asymmetric? Give reasons for your answers.

### Solution
For a relation $R$ on a set $A$ 
	- asymmetric if $(a, b) \in R$ implies that $(b, a) \notin R$, 
	- antisymmetric if $a=b$ whenever $(a, b),(b, a) \in R$.
  
Every asymmetric relation is antisymmetric. 
**Proof:** Suppose $R$ is an asymmetric relation on a set $A$.
Let $(a, b) \in R$. Then, $a \neq b$ and $(b, a) \notin R$.
Hence, $R$ is anti - symmetric.