---
title: Formulas and Identities
description: Useful summation closed forms, laws, identities, and any relevant proofs
published: true
date: 2021-08-22T00:45:16.214Z
tags: mathematics
editor: markdown
---

# Laws
## Distributive Law (Factoring out constants)
$$
\sum_{\mathrm{k} \in \mathrm{K}} \mathrm{c} a_{k}=\mathrm{c} \sum_{\mathrm{k} \in \mathrm{K}} a_{k}
$$
or 
$$
\sum_{i=a}^{b} c f(i)=c \sum_{i=a}^{b} f(i)
$$
Note: $c$ is some constant.
Allows us to move constants in and out of a $\Sigma$.

If $\mathrm{K}=\{-1,0,+1\} \text { and if } p(\mathrm{k})=-\mathrm{k}$,
$\mathrm{ca}_{-1}+\mathrm{ca}_{0}+\mathrm{ca}_{1}=\mathrm{c}\left(\mathrm{a}_{-1}+\mathrm{a}_{0}+\mathrm{a}_{1}\right)$
## Associative Law (Splitting and combining sums)
$$
\sum_{\mathrm{k} \in \mathrm{K}}\left(a_{\mathrm{k}}+\mathrm{b}_{\mathrm{k}}\right)=\sum_{\mathrm{k} \in \mathrm{K}} a_{\mathrm{k}}+\sum_{\mathrm{k} \in \mathrm{K}} \mathrm{b}_{k}
$$

Or 

$$
\sum_{i=a}^{b}(x+y)=\sum_{i=a}^{b} x+\sum_{i=a}^{b} y
$$

Allows us to break a $\Sigma$ into two parts, or to combine two $\Sigma$'s into one.

If $\mathrm{K}=\{-1,0,+1\} \text { and if } p(\mathrm{k})=-\mathrm{k}$,

$\left(a_{-1}+b_{-1}\right)+\left(a_{0}+b_{0}\right)+\left(a_{1}+b_{1}\right)$
$\quad=\left(a_{-1}+a_{0}+a_{1}\right)+\left(b_{-1}+b_{0}+b_{1}\right)$
## Commutative Law
$$
\sum_{k \in K} a_{k}=\sum_{p(k) \in K} a_{p(k)}
$$

Says we can reorder terms in any way we please. 


If $\mathrm{K}=\{-1,0,+1\} \text { and if } p(\mathrm{k})=-\mathrm{k}$, 
$a_{-1}+a_{0}+a_{1}=a_{1}+a_{0}+a_{-1}$.

## Interchanging the Order of Summation Law
### For when the indexes of summation are independent of eachother
This is a generalization of the associative law, for use in evaluating a sum of sums. This vanilla version applies whenever the ranges of $j$ and $k$ are independent of eachother.

$$
\sum_{j} \sum_{k} a_{j, k}[P(j, k)]=\sum_{P(j, k)} a_{j, k}=\sum_{k} \sum_{j} a_{j, k}[P(j, k)]
$$

Another way to write the above is 
$$
\sum_{j \in J} \sum_{k \in K} a_{j, k}=\sum_{j \in J \atop k \in K} a_{j, k}=\sum_{k \in K} \sum_{j \in J} a_{j, k}
$$

### For when the range of an inner sum depends on the index variable of the outer sum
$$
\sum_{j \in J} \sum_{k \in K(j)} a_{j, k}=\sum_{k \in K^{\prime}} \sum_{j \in J^{\prime}(k)} a_{j, k}
$$

Here the sets $J, K(j), K^{\prime}$, and $J^{\prime}(k)$ must be related in such a way that
$$
[j \in J][k \in K(j)]=\left[k \in K^{\prime}\right]\left[j \in J^{\prime}(k)\right]
$$
