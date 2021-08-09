---
title: Sigma Notation and Summations
description: 
published: true
date: 2021-08-09T19:08:33.137Z
tags: mathematics, discrete-mathematics
editor: markdown
---

$$
a_{m}, a_{m+1}, \ldots, a_{n}
$$

from the sequence $\left\{a_{n}\right\}$. We use the notation
$$
\sum_{j=m}^{n} a_{j}, \quad \sum_{j=m}^{n} a_{j}, \quad \text { or } \quad \sum_{m \leq j \leq n} a_{j}
$$
(read as the sum from $j=m$ to $j=n$ of $a_{j}$ ) to represent
$$
a_{m}+a_{m+1}+\cdots+a_{n}
$$

Above, the variable $j$ is called the **index of summation**. The choice of $j$ is arbitrary, we could have used any letter, such as $i$ or $k$.. 

$$
\sum_{j=m}^{n} a_{j}=\sum_{i=m}^{n} a_{i}=\sum_{k=m}^{n} a_{k}
$$

Here, the index of summation runs through all integers with its **lower limit** $m$ and ending with its **upper limit** $n$ (both inclusive).

# Generalized Sigma Notation
$$
\sum_{1 \leqslant k \leqslant n} a_{k}
$$
Above, an inequality is used to specify the set of indices over which the summation should take place. 

## Advantage of Generalized Sigma Notation
It can be manipulated more easily than the delimited form. 

For example, suppose we want to change the index variable $k$ to $k+1$. With the general form, we have

$$
\sum_{1 \leqslant k \leqslant n} a_{k}=\sum_{1 \leqslant k+1 \leqslant n} a_{k+1}
$$

Compare that to the delimited form, where its more confusing to see whats happening..

$$
\sum_{k=1}^{n} a_{k}=\sum_{k=0}^{n-1} a_{k+1}
$$
## Example of a General Sum and It's Delimited Equivalent
For example, we can express the sum of squares of all odd positive integers below $100$ as follows: 

$$
\sum_{1 \leqslant k<100 \atop k \text { odd }} k^{2}
$$

The delimited equivalent is 
$$
\sum_{k=0}^{49}(2 k+1)^{2}
$$

# Sums and Recurrences
The sum
$$
\mathrm{S}_{\mathrm{n}}=\sum_{\mathrm{k}=0}^{\mathrm{n}} a_{\mathrm{k}}
$$

is equivalent to the recurrence

$$
\begin{aligned}
S_{0} &=a_{0} ; \\
S_{n} &=S_{n-1}+a_{n}, \quad \text { for } n>0
\end{aligned}
$$

If $a_n$ os equal to a constant plus a multiple of $n$, the recurrence above takes the following form: 

$$
\begin{array}{l}
R_{0}=\alpha \\
R_{n}=R_{n-1}+\beta+\gamma n, \quad \text { for } n>0 .
\end{array}
$$

We find $R_{1}=\alpha+\beta+\gamma, R_{2}=\alpha+2 \beta+3 \gamma$, and so on; in general the solution can be written in the form

$$
R_{n}=A(n) \alpha+B(n) \beta+C(n) \gamma
$$

where $A(n), B(n)$, and $C(n)$ are the coefficients of dependence on the general parameters $\alpha, \beta$, and $\gamma$.




# Formula for the Sum of Terms of a Geometric Progression
Recall that sums of geometric progressions are called **geometric series**. 
If $a$ and $r$ are real numbers and $r \neq 0$, then
$$
\sum_{j=0}^{n} a r^{j}=\left\{\begin{array}{ll}
\frac{a r^{n+1}-a}{r-1} & \text { if } r \neq 1 \\
(n+1) a & \text { if } r=1
\end{array}\right.
$$

## Proof
Let 
$$S_{n}=\sum_{j=0}^{n} a r^{j}$$

To compute $S$, first multiply both sides of the equality by $r$ and then manipulate the resulting sum as follows:

1. Substitute Summation formula for $S$
$$r S_{n}=r \sum_{j=0}^{n} a r^{j}$$

2. by the distributive property
$$
=\sum_{j=0}^{n} a r^{j+1}
$$
3. Shifting the index of summation, with $k=k+1$
$$
=\sum_{k=1}^{n+1} a r^{k}
$$
4. Removing $k=n+1$ term and adding $k=0$ term
$$
=\left(\sum_{k=0}^{n} a r^{k}\right)+\left(a r^{n+1}-a\right)
$$
5. Substituting $S$ for summation formula
$$
=S_{n}+\left(a r^{n+1}-a\right)
$$

From these equalities, we see that
$$
r S_{n}=S_{n}+\left(a r^{n+1}-a\right)
$$
Solving for $S_{n}$ shows that if $r \neq 1$, then
$$
S_{n}=\frac{a r^{n+1}-a}{r-1}
$$
If $r=1$, then the $S_{n}=\sum_{j=0}^{n} a r^{j}=\sum_{j=0}^{n} a=(n+1) a$
$$\hspace {32em} \blacksquare$$



# Manipulating Sums
## Laws
### Distributive Law
$$
\sum_{\mathrm{k} \in \mathrm{K}} \mathrm{c} a_{k}=\mathrm{c} \sum_{\mathrm{k} \in \mathrm{K}} a_{k}
$$

Allows us to move constants in and out of a $\Sigma$.

If $\mathrm{K}=\{-1,0,+1\} \text { and if } p(\mathrm{k})=-\mathrm{k}$,
$\mathrm{ca}_{-1}+\mathrm{ca}_{0}+\mathrm{ca}_{1}=\mathrm{c}\left(\mathrm{a}_{-1}+\mathrm{a}_{0}+\mathrm{a}_{1}\right)$
### Associative Law
$$
\sum_{\mathrm{k} \in \mathrm{K}}\left(a_{\mathrm{k}}+\mathrm{b}_{\mathrm{k}}\right)=\sum_{\mathrm{k} \in \mathrm{K}} a_{\mathrm{k}}+\sum_{\mathrm{k} \in \mathrm{K}} \mathrm{b}_{k}
$$
Allows us to break a $\Sigma$ intwo two parts, or to combine two $\Sigma$'s into one.

If $\mathrm{K}=\{-1,0,+1\} \text { and if } p(\mathrm{k})=-\mathrm{k}$,

$\left(a_{-1}+b_{-1}\right)+\left(a_{0}+b_{0}\right)+\left(a_{1}+b_{1}\right)$
$\quad=\left(a_{-1}+a_{0}+a_{1}\right)+\left(b_{-1}+b_{0}+b_{1}\right)$
### Commutative Law
$$
\sum_{k \in K} a_{k}=\sum_{p(k) \in K} a_{p(k)}
$$

Says we can reorder terms in any way we please. 


If $\mathrm{K}=\{-1,0,+1\} \text { and if } p(\mathrm{k})=-\mathrm{k}$, 
$a_{-1}+a_{0}+a_{1}=a_{1}+a_{0}+a_{-1}$.

### Interchanging the Order of Summation Law
#### For when the indexes of summation are independent of eachother
This is a generalization of the associative law, for use in evaluating a sum of sums. This vanilla version applies whenever the ranges of $j$ and $k$ are independent of eachother.

$$
\sum_{j} \sum_{k} a_{j, k}[P(j, k)]=\sum_{P(j, k)} a_{j, k}=\sum_{k} \sum_{j} a_{j, k}[P(j, k)]
$$

Another way to write the above is 
$$
\sum_{j \in J} \sum_{k \in K} a_{j, k}=\sum_{j \in J \atop k \in K} a_{j, k}=\sum_{k \in K} \sum_{j \in J} a_{j, k}
$$

#### For when the range of an inner sum depends on the index variable of the outer sum
$$
\sum_{j \in J} \sum_{k \in K(j)} a_{j, k}=\sum_{k \in K^{\prime}} \sum_{j \in J^{\prime}(k)} a_{j, k}
$$

Here the sets $J, K(j), K^{\prime}$, and $J^{\prime}(k)$ must be related in such a way that
$$
[j \in J][k \in K(j)]=\left[k \in K^{\prime}\right]\left[j \in J^{\prime}(k)\right]
$$
### Use of the laws
Suppose we want to compute the general sum of an arithmetic progression, 
$$
S=\sum_{0 \leqslant k \leqslant n}(a+b k)
$$

By the commutative law we can replace $k$ by $n-k$, obtaining 
$$
S=\sum_{0 \leqslant n-k \leqslant n}(a+b(n-k))=\sum_{0 \leq k \leq n}(a+b n-b k)
$$

Note that 

$$
\sum_{0 \leq k \leq n}(a+b k)=(a+0 \cdot b)+(a+1 \cdot b)+\cdots+(a+(n-1) \cdot b)+(a+n \cdot b)
$$

and 

$$
\sum_{0 \leq k \leq n}(a+(n-k) b)=(a+(n-0) \cdot b)+(a+(n-1) \cdot b)+\cdots+(a+(n-(n-1)) \cdot b) \\
+(a+(n-n) \cdot b)
$$

so one sum is just the reversal of the other.

The two equations can be added together using the associative law:
$$
2 S=\sum_{0 \leqslant k \leqslant n}((a+b k)+(a+b n-b k))=\sum_{0 \leqslant k \leqslant n}(2 a+b n)
$$

And we can now apply the distributive law and evaluate a trival sum:
$$
2 S=(2 a+\text { bn }) \sum_{0 \leqslant k \leqslant n} 1=(2 a+b n)(n+1)
$$

Dividing by $2$, we have proved that 
$$
\sum_{k=0}^{n}(a+b k)=\left(a+\frac{1}{2} b n\right)(n+1)
$$
## Shifting the Index of Summation
Sometimes its useful to shift the index of summation in a sum. This is often done when two sums need to be added but their indices of summation do not match. When shifting an index of summation, it is important to make the appropriate changes in the corresponding summand. 

### Example
Suppose we have the sum 
$$\sum_{j=1}^{5} j^{2}$$
but want the index of summation to run between $0$ and $4$ rather than $1$ to $5$. To do this, we let $k=j-1$. Then the new summation index runs from 0 (because $k=1-0=0$ when $j=1$ ) to 4 (because $k=5-1=4$ when $j=5$ ), and the term $j^{2}$ becomes $(k+1)^{2}$. Hence,
$$
\sum_{j=1}^{5} j^{2}=\sum_{k=0}^{4}(k+1)^{2}
$$


# Useful Summation Closed Forms

$$
\begin{array}{|c|c|}
\hline \text { Sum } & \text { Closed Form } \\
\hline \sum_{k=0}^{n} a r^{k}(r \neq 0) & \frac{a r^{n+1}-a}{r-1}, r \neq 1 \\[1em]
\sum_{k=1}^{n} k & \frac{n(n+1)}{2} \\[1em]
\sum_{k=1}^{n} k^{2} & \frac{n(n+1)(2 n+1)}{6} \\[1em]
\sum_{k=1}^{n} k^{3} & \frac{n^{2}(n+1)^{2}}{4} \\[1em]
\sum_{k=0}^{\infty} x^{k},|x|<1 & \frac{1}{1-x} \\[1em]
\sum_{k=1}^{\infty} k x^{k-1},|x|<1 & \frac{1}{(1-x)^{2}} \\
\hline
\end{array}
$$



# Linearity
For any real number $c$ and any finite sequences $a_{1}, a_{2}, \ldots, a_{n}$ and $b_{1}, b_{2}, \ldots, b_{n}$,
$\sum_{k=1}^{n}\left(c a_{k}+b_{k}\right)=c \sum_{k=1}^{n} a_{k}+\sum_{k=1}^{n} b_{k} .$


## Splitting Summations
$$
\sum(A+B)=\left(\sum A\right)+\left(\sum B\right)
$$

For example
$$
\sum_{k=1}^{n}(k+2)=\left(\sum_{k=1}^{n} k\right)+\left(\sum_{k=1}^{n} 2\right)
$$

# Multiple Summations

Terms of a sum may be specified by two or more indices. For example, here is a double sum of nine terms, governed by two indices $j$ and $k$. 

$$
\begin{aligned}
\sum_{1 \leqslant j, k \leqslant 3} a_{j} b_{k}=& a_{1} b_{1}+a_{1} b_{2}+a_{1} b_{3} \\
&+a_{2} b_{1}+a_{2} b_{2}+a_{2} b_{3} \\
&+a_{3} b_{1}+a_{3} b_{2}+a_{3} b_{3}
\end{aligned}
$$

The same notations and methods for single summations are used for multiple summations. Thus, if $\mathrm{P}(j, \mathrm{k})$ is a property of $\mathrm{j}$ and $\mathrm{k}$, the sum of all terms $a_{j, k}$ such that $P(j, k)$ is true can be written in two ways, one of which uses Iverson's convention and sums over all pairs of integers $j$ and $k$ :
$$
\sum_{\mathrm{P}(\mathrm{j}, \mathrm{k})} a_{j, k}=\sum_{j, k} a_{j, k}[\mathrm{P}(j, k)]
$$

## Sum of Sums
Two $\Sigma$'s are used when we are talking about a sum of sums. For example,
$$
\sum_{j} \sum_{k} a_{j, k}[P(j, k)]
$$
is an abbreviation for 

$$
\sum_{j}\left(\sum_{k} a_{j, k}[P(j, k)]\right)
$$

## Double Summation example

$$
\begin{aligned}
\sum_{1 \leqslant j, k \leqslant 3} a_{j} b_{k} &=\sum_{j, k} a_{j} b_{k}[1 \leqslant j, k \leqslant 3]=\sum_{j, k} a_{j} b_{k}[1 \leqslant j \leqslant 3][1 \leqslant k \leqslant 3] \\
&=\sum_{j} \sum_{k} a_{j} b_{k}[1 \leqslant j \leqslant 3][1 \leqslant k \leqslant 3] \\
&=\sum_{j} a_{j}[1 \leqslant j \leqslant 3] \sum_{k} b_{k}[1 \leqslant k \leqslant 3] \\
&=\sum_{j} a_{j}[1 \leqslant j \leqslant 3]\left(\sum_{k} b_{k}[1 \leqslant k \leqslant 3]\right) \\
&=\left(\sum_{j} a_{j}[1 \leqslant j \leqslant 3]\right)\left(\sum_{k} b_{k}[1 \leqslant k \leqslant 3]\right) \\
&=\left(\sum_{j=1}^{3} a_{j}\right)\left(\sum_{k=1}^{3} b_{k}\right) .
\end{aligned}
$$

First line denotes a sum of nine terms in no particular orer.

Second line groups them in threes, $\left(a_{1} b_{1}+a_{1} b_{2}+a_{1} b_{3}\right)+\left(a_{2} b_{1}+a_{2} b_{2}+ \left.a_{2} b_{3}\right)+\left(a_{3} b_{1}+a_{3} b_{2}+a_{3} b_{3}\right)\right.$.

The third line uses the distributive law to factor out the a's, since $a_{j}$ and $[1 \leqslant j \leqslant 3]$ do not depend on $k ;$ this gives $a_{1}\left(b_{1}+b_{2}+b_{3}\right)+a_{2}\left(b_{1}+b_{2}+b_{3}\right)+a_{3}\left(b_{1}+b_{2}+b_{3}\right) .$

The fourth line is the same as the third, but with a redundant pair of parentheses thrown in so that the  fth line won't look so mysterious.

The fifth line factors out $\left(b_{1}+b_{2}+b_{3}\right)$ that occurs for each value of $j:\left(a_{1}+a_{2}+a_{3}\right)\left(b_{1}+b_{2}+b_{3}\right)$
The last line is just another way to write the previous line. 

This method of derivation can be used to prove a general distributive law,

$$
\sum_{j \in J \atop k \in K} a_{j} b_{k}=\left(\sum_{j \in J} a_{j}\right)\left(\sum_{k \in K} b_{k}\right)
$$

valid for all sets of indices $J$ and $K$.

## Double Summation Example 2
To evaluate the double sum, first expand the inner summation and then continue by computing
the outer summation:
$$
\begin{aligned}
\sum_{i=1}^{4} \sum_{j=1}^{3} i j &=\sum_{i=1}^{4}(i+2 i+3 i) \\
&=\sum_{i=1}^{4} 6 i \\
&=6+12+18+24=60 .
\end{aligned}
$$