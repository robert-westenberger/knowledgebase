---
title: Random notes
description: 
published: true
date: 2022-02-26T23:22:43.260Z
tags: 
editor: markdown
---

# Random notes

I was reading the following two resources about summation identities:
1) Concrete Mathematics: A Foundation for Computer Science (2nd Ed) by Knuth and Patashnik section 2.3 Manipulation of Sums
2) this other resource [here][1] on summation algebra I randomly came across googling. 


CM is calling the **Distributive Law** as follows:

$\sum_{k \in K} c a_{k}=c \sum_{k \in K} a_{k}$

but the book on the algebra of summations calls it  **"The Second Constant Rule"**

$\sum_{i=1}^{N} a x_{i}=a \sum_{i=1}^{N} x_{i}$


CM is calling the **Associative Law** as follows:

$\sum_{k \in K}\left(a_{k}+b_{k}\right)=\sum_{k \in K} a_{k}+\sum_{k \in K} b_{k}$

but the other resource calls it **"The Distributive Rule of Summation Algebra"**

$\sum_{i=1}^{N}\left(x_{i}+y_{i}\right)=\sum_{i=1}^{N} x_{i}+\sum_{i=1}^{N} y_{i}$

I can see how **"The Second Constant Rule"** is 



  [1]: http://www.statpower.net/Content/310/Summation%20Algebra.pdf
  
  
# random 2
RTK usequery hook should return a singly nested object. Any more nesting than one layer, or having values besides simple primitives in an object, will cause unnecessary rerenders because react can't diff them. Reading from store state should happen further down the tree.

