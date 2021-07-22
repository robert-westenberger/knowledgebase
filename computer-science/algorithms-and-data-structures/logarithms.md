---
title: Logarithms
description: 
published: true
date: 2021-07-22T17:55:31.811Z
tags: mathematics, algorithms
editor: markdown
---

A **logarithm** is simply an inverse exponential function. Saying $b^{x}=y$ is equivalent to saying that $x=\log _{b} y .$ Further, this equivalence is the same as saying $b^{\log _{b} y}=y$. (The $b$ term is known as the **base** of the logarithm).

Logarithms arise in any process where things are repeatedly halved.

# Properties of Logarithms
## Important Bases
Three bases are of particular importance for mathematical and historical reasons:
* Base $b=2$ : The binary logarithm, usually denoted $\lg x$, is a base 2 logarithm. We have seen how this base arises whenever repeated halving (i.e., binary search) or doubling (i.e., nodes in trees) occurs. Most algorithmic applications of logarithms imply binary logarithms.
* Base $b=e:$ The natural logarithm, usually denoted $\ln x$, is a base $e=$ $2.71828 \ldots$ logarithm. The inverse of $\ln x$ is the exponential function $\exp (x)=e^{x}$ on your calculator. Thus, composing these functions gives us the identity function,
$$
\exp (\ln x)=x \text { and } \ln (\exp x)=x
$$

* Base $b=10$ : Less common today is the base- 10 or common logarithm, usually denoted as $\log x$. This base was employed in slide rules and logarithm books in the days before pocket calculators.

## Important Properties
* **Product Rule**  $\log _{a}(x y)=\log _{a}(x)+\log _{a}(y)$ - The log of a product is equal to the sum of the logs of its factors.
* **Change of base rule**  $\log _{a} b=\frac{\log _{c} b}{\log _{c} a}$ - Changing the base of $\log b$ from base-$a$ to base-$c$ involves multiplying by $\log _{c} a$.
# Logarithms, Trees, and Bits
![tree_fig.png](/tree_fig.png)
A height $h$ tree with $d$ children per node has $d^{h}$ leaves. Here $h=3$ and $d=3$ (left). The number of bit patterns grows exponentially with pattern length (right). These would be described by the root-to-leaf paths of a binary tree of height $h=3$.

There are two bit patterns of length $1(0$ and 1$)$, four of length $2(00,01,10$, and 11), and eight of length 3 (see right of above image). How many bits $w$ do we need to represent any one of $n$ different possibilities, be it one of $n$ items or the integers from 0 to $n-1 ?$

The key observation is that there must be at least $n$ different bit patterns of length $w$. Since the number of different bit patterns doubles as you add each bit, we need at least $w$ bits where $2^{w}=n$. In other words, we need $w=\log _{2} n$ bits.

# Logarithms and Multiplication
Logarithms are useful for multiplication, particularly for exponentiation. 

Recall that $\log _{a}(x y)=\log _{a}(x)+\log _{a}(y) ;$ that is, the log of a product is the sum of the logs. A direct consequence of this is
$$
\log _{a} n^{b}=b \cdot \log _{a} n
$$
How can we compute $a^{b}$ for any $a$ and $b$ using the $\exp (x)$ and $\ln (x)$ functions on your calculator, where $\exp (x)=e^{x}$ and $\ln (x)=\log _{e}(x) ?$ We know
$$
a^{b}=\exp \left(\ln \left(a^{b}\right)\right)=\exp (b \ln (a))
$$
so the problem is reduced to one multiplication plus one call to each of these functions.

# Fast Exponentiation
Logarithms can be used to quickly give an exact computation of the value of $a^n$. The simplest algorithm performs $n-1$ multiplications, by computing $a \times a \times$ $\ldots \times a .$ However, we can do better by observing that $n=\lfloor n / 2\rfloor+\lceil n / 2\rceil .$ If $n$ is even, then $a^{n}=\left(a^{n / 2}\right)^{2}$. If $n$ is odd, then $a^{n}=a\left(a^{\lfloor n / 2\rfloor}\right)^{2}$. In either case, we have halved the size of our exponent at the cost of, at most, two multiplications, so $O(\lg n)$ multiplications suffice to compute the final value.

The below algorithm illustrates the importance of divide and conquer. 
<pre>
function power(a, n)
	if (n = 0) return(1)
	x = power(a,  n/2 )
	if (n is even) then return(x2)
		else return(a   x2)
</pre>

# Logarithms and Summations
The **Harmonic numbers** arise as a special case of a sum of a power of integers. They are the sum of the progerssion of simple reciprocals, namely, 

$$
H(n)=\sum_{i=1}^{n} 1 / i=\Theta(\log n)
$$

Harmonic numbers are important because they usually explain "where the log comes from". For example, the key to analyzing the average-case complexity of quicksort is the summation $n \sum_{i=1}^{n} 1 / i$. 