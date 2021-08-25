---
title: Formulas and Identities
description: Useful summation closed forms, laws, identities, and any relevant proofs
published: true
date: 2021-08-25T17:19:31.740Z
tags: mathematics
editor: markdown
---

# Laws and Identities
## Distributive Law (Factoring out constants)
$$
\sum_{\mathrm{k} \in \mathrm{K}} \mathrm{c} a_{k}=\mathrm{c} \sum_{\mathrm{k} \in \mathrm{K}} a_{k}
$$
$$\textbf{or}$$

$$
\sum_{i=a}^{b} c f(i)=c \sum_{i=a}^{b} f(i)
$$
**Note:** $c$ is some constant.
Allows us to move constants in and out of a $\Sigma$.

If $\mathrm{K}=\{-1,0,+1\} \text { and if } p(\mathrm{k})=-\mathrm{k}$,
$\mathrm{ca}_{-1}+\mathrm{ca}_{0}+\mathrm{ca}_{1}=\mathrm{c}\left(\mathrm{a}_{-1}+\mathrm{a}_{0}+\mathrm{a}_{1}\right)$
## Associative Law (Splitting and combining sums)
$$
\sum_{\mathrm{k} \in \mathrm{K}}\left(a_{\mathrm{k}}+\mathrm{b}_{\mathrm{k}}\right)=\sum_{\mathrm{k} \in \mathrm{K}} a_{\mathrm{k}}+\sum_{\mathrm{k} \in \mathrm{K}} \mathrm{b}_{k}
$$

$$\textbf{or}$$

$$
\sum_{i=a}^{b}(x+y)=\sum_{i=a}^{b} x+\sum_{i=a}^{b} y
$$

$$\textbf{or}$$

$$
\sum(A+B)=\left(\sum A\right)+\left(\sum B\right)
$$

Allows us to break a $\Sigma$ into two parts, or to combine two $\Sigma$'s into one.

If $\mathrm{K}=\{-1,0,+1\} \text { and if } p(\mathrm{k})=-\mathrm{k}$,

$\left(a_{-1}+b_{-1}\right)+\left(a_{0}+b_{0}\right)+\left(a_{1}+b_{1}\right)$
$\quad=\left(a_{-1}+a_{0}+a_{1}\right)+\left(b_{-1}+b_{0}+b_{1}\right)$
### Special Note: Products and Quotients Can't Be Split!
$$
\sum_{i=i_{0}}^{n}\left(a_{i} b_{i}\right) \neq\left(\sum_{i=i}^{n} a_{i}\right)\left(\sum_{i=i_{0}}^{n} b_{i}\right)
$$

and

$$
\sum_{i=i_{0}}^{n} \frac{a_{i}}{b_{i}} \neq \frac{\sum_{i=i_{0}}^{n} a_{i}}{\sum_{i=i_{0}}^{n} b_{i}}
$$

## Commutative Law (Reordering Terms)
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

## Adjusting Summation Bounds
$$
\sum_{i=a}^{b} f(x)=\sum_ {i=0}^{b} f(x)-\sum_{i=0}^{a-1} f(x)
$$

$$\textbf{or}$$

$$
\sum_{n=s}^{t} f(n)=\sum_{n=s+p}^{t+p} f(n-p)
$$
# Useful Closed Forms


$$
\begin{array}{|c|c|}
\hline \text { Sum } & \text { Closed Form } \\
\hline \sum_{k=0}^{n} a r^{k}(r \neq 0) & \frac{a r^{n+1}-a}{r-1}, r \neq 1 \\[1em]
\sum_{k=1}^{n} c & cn \\[1em]
\sum_{k=1}^{n} k & \frac{n(n+1)}{2} \\[1em]
\sum_{k=1}^{n} k^{2} & \frac{n(n+1)(2 n+1)}{6} \\[1em]
\sum_{k=1}^{n} k^{3} & \frac{n^{2}(n+1)^{2}}{4} \\[1em]
\sum_{k=0}^{\infty} x^{k},|x|<1 & \frac{1}{1-x} \\[1em]
\sum_{k=1}^{\infty} k x^{k-1},|x|<1 & \frac{1}{(1-x)^{2}} \\
\hline
\end{array}
$$