---
title: Well Ordering Principle
description: 
published: true
date: 2021-03-07T02:15:40.791Z
tags: mathematics, discrete-mathematics
editor: markdown
---

The Well Ordering Principle is
$$
\text { Every nonempty set of nonnegative integers has a smallest element. }
$$

or 
$$
\text { Every nonempty subset of } \mathbb{N} \text { has a smallest element. }
$$
note how it only applies to sets with nonnegative integers.


## Using WOP to prove $\sqrt 2$ is irrational
By the WOP, we can assume that for any positive integers $m$ and $n$,  the fraction $m/n$ can be written in lowest terms.. in the form $m^{\prime} / n^{\prime}$ where $m^{\prime}$ and $n^{\prime}$ are positive integers with no common prime factors. How do we know this is possible?

Suppose to the contrary that there are positive integers $m$ and $n$ such that the fraction $m/n$ cannot be written in lowest terms. 

Let $C = \{ \text{positive integers that are numerators of such fractions} \}$.

Then $m \in C$ so $C$ is nonempty.

By WOP, there must be a smallest integer $m_0 \in C$.

By definition of $C$, there is an integer $n_0 \gt 0$ such that 
$$
\text { the fraction } \frac{m_{0}}{n_{0}} \text { cannot be written in lowest terms. }
$$

This means that $m_0$ and $n_0$ must have a common prime factor, $p \gt 1$, but

$$
\frac{m_{0} / p}{n_{0} / p}=\frac{m_{0}}{n_{0}}
$$

so any way of expressing the left-hand fraction in lowest terms would also work for $m_{0} / n_{0}$, which implies
$$
\text { the fraction } \frac{m_{0} / p}{n_{0} / p} \text { cannot be in written in lowest terms either. }
$$

So by definition of $C$, the numerator $m_{0} / p$ is in $C$. But $m_{0} / p<m_{0}$m which contradicts the fact that $m_0$ is the smallest element of $C$.

Since the assumption that $C$ is nonempty leads to a contradiction, it follows that $C$ must be empty. That is, there are no numerators of fractions that can't be written in lowest terms, and hence there are no such fractions at all.
# Template Well Ordering Proofs
Standard way to prove that $P(n)$ holds for every nonnegative integer $n$ ( "$P(n)$ is true for all $n \in \natnums$".

* Define the set $C$ of counterexamples to $P$ being true. Specifically, define

$$
C\Coloneqq\{n \in \mathbb{N} \mid \operatorname{NOT}(P(n)) \text { is true }\}
$$
(The notation $\{n \mid Q(n)\}$ means that "the set if all elements $n$ for which $Q(n)$ is true.")

* Assume for proof by contradiction that $C$ is nonempty.

* By WOP, there will be a smallest element $n$ in $C$. 

* Reach a contradiction somehow - often by showing that $P(n)$ is actually true or by showing that there is another member of $C$ that is smaller than $n$. This is the open ended part of the proof task.

* Conclude that $C$ must be empty, that is, no counterexamples exist.

## Factoring into Primes
### Prime Factorization Theorem / Unique Factorization Theorem / Fundamental Theorem of Arithmetic
Every integer greater than one has a unique^1^ expression as a product of prime numbers.

^1^ - Unique up to the order in which the prime factors appear.


#### Proof of Prime Factorization Theorem
**Theorem:** Every positive integer greater than one can be factored as a product of primes. 

**Proof:** This proof is by WOP.

Let $C$ be the set of all integers greater than one that can't be factored as a product of primes. We assume $C$ is not empty and derive a contradiction.

If $C$ is not empty, there is a least element $n \in C$ by WOP. This $n$ can't be prime, because a prime by itself is considered a (length one) product of primes, and no such products are in $C$.

So $n$ must be a product of two integers $a$ and $b$ where $a \gt 1$ and $b \lt n$. 

Since $a$ and $b$ are smaller than the smallest element in $C$, we know that $a,b \notin C$. 

In other words, $a$ can be written as a product of primes $p_{1} p_{2} \cdots p_{k}$ and $b$ as a product of primes $q_{1} \cdots q_{l}$. 

Therefore, $n=p_{1} \cdots p_{k} q_{1} \cdots q_{l}$ can be written as a product of primes, contradicting the claim that $n \in C$. Our assumption that $C$ is not empty must therefore be false.
$$\hspace{32em} \blacksquare$$
## Well Ordered Sets
Well ordering cokmmonly comes up in computer science as a method for proving that computations won't run forever. The idea is to assign a value to each successive step of a computation so that the values get smaller at every step. If the values are all from a well ordered set, then the computation can't run forever, because if it did, the values assigned to its successive steps would define a subset with no minimum element.

Notice that a set may have a minimum element but not be well ordered. The set of nonnegative rational numbers is an example: is has a minimum element zero, but it also has nonempty subsets that don't have minimum elements - the positive rationals, for example. 

The following theorem is a generalization of the WOP: "For any nonnegative integer $n$ the set of integers greater than or equal to $-n$ is well ordered." (Proven in example section below)

The definition of well ordering states that every subset of a well ordered set is well ordered, and this yields two convenient corollaries to the generalized theorem above (proved in the examples section below): 

A lower bound for a set $S$ of real numbers is a number $b$ such that $b \leq s$ for every $s \in S$.

A upper bound for a set $S$ of real numbers is a number $b$ such that $b \geq s$ for every $s \in S$.
(Note that a lower or upper bound of set $S$ is not required to be in the set)

**Corollary 1:** Any set of integers with a lower bound is well ordered.
**Corollary 2:** Any nonempty set of integers with an upper bound has a maximum element.
## Other WOP Proofs Examples
### Example (Tiny generalization of WOP)
**Theorem:**
For any nonnegative integer $n$ the set of integers greater than or equal to $-n$ is well ordered.
**Proof:**
Let $S$ be any nonempty set of integers $\ge -n$. Now add $n$ to each of the elements in $S$; lets call this new set $S + n$. Now $S + n$ is a nonempty set of nonnegative integers, and so by WOP, it has a minimum element $m$. Then it is easy to see $m-n$ is the minimum element of $S$.
$$\hspace{32em} \blacksquare$$

### Example (Corollary 1)
**Theorem:** Any set of integers with a lower bound is well ordered.
**Proof:** 
A set of integers with a lower bound $b \in \reals$ will also have an integer $n=\lfloor b\rfloor$ as a lower bound, where $\lfloor b\rfloor$, called the floor of $b$, is gotten by rounded down $b$ to the nearest integer. So the theorem "For any nonnegative integer $n$ the set of integers greater than or equal to $-n$ is well ordered." implies the set is well ordered.
$$\hspace{32em} \blacksquare$$
### Example (Corollary 2)
**Theorem:** Any nonempty set of integers with an upper bound has a maximum
element.
**Proof:**
Suppose a set of $S$ integers has an upper bound $b \in \reals$.
### Example
**Theorem:**
$$
\sum_{i=1}^{n} i = \frac{n(n+1)} 2
$$
for all nonnegative integers $n$.

**Proof:**
By contradiction. Assume the theorem is false. Then, some nonnegative integers serve as counterexamples ot it. Collected in a set:

$$
C::=\left\{n \in \mathbb{N} \mid 1+2+3+\cdots+n \neq \frac{n(n+1)}{2}\right\}
$$

(set C is defined as the set of natural numbers $n$ that when added up don't equal $\frac{n(n+1)} 2$. 

Assuming there are counter examples, $C$ is a nonempty set of nonnegative integers. 

By WOP, $C$ has a minimum element which is the smallest counterexample, $c$.

Since $c$ is the smallest counterexample, we know that our theorem is false for $n=c$ but true for all nonegative integers $n \lt c$. But our theorem is true for $n=0$, so $c \gt 0$. This means that $c-1$ is a nonnegative integer, and since it it less than $c$, our theorem is true for $c-1$. That is, 
$$
1+2+3+\cdots+(c-1)=\frac{c(c-1)}{2}
$$

Adding $c$ to both sides, we get 

$$
1+2+3+\cdots+(c-1)+c=\frac{c(c-1)}{2}+c=\frac{c^{2}-c+2 c}{2}=\frac{c(c+1)}{2}
$$

which means that our theorem does hold for $c$ afer all. This is a contradiction, and we are done. 
$$\hspace{32em} \blacksquare$$

