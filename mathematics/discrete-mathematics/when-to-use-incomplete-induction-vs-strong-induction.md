---
title: Strong Induction vs Induction vs Well Ordering
description: 
published: true
date: 2021-04-26T17:25:22.240Z
tags: discrete-mathematics
editor: markdown
---

# When To Use Incomplete Induction
Use mathematical induction when it is straightforward to prove that $P(k) \rarr P(k+1)$ is true for all positive integers $k$. 

# When To Use Strong Induction
When you see how to prove $P(k+1)$ is true from the assumption that $P(j)$ is true for all positive integers $j$ not exceeding $k$, but yo ucannot see how to prove that $P(k+1)$ follows from just $P(k)$.

# Examples of Strong Induction (and why the use of Strong Induction was required)

## Proof of the fundamental theorem of arithmetic
Show that if $n$ is an integer greater than $1$, then $n$ can be written as the product of primes.


Let $P(n)$ be the proposition that $n$ can be written as the product of primes. 

**Basis Step:** $P(2)$ is true because $2$ can be written as the product of one prime, itself.

**Inductive Step:** The inductive hypothesis is assumption that $P(j)$ is true for all integers $j$ with $2 \le j \le k$. That is, $j$ can be written as the product of primes whenver $j$ is a positive integer at least $2$ and not exceeding $k$. 

To complete the inductive step, it must be shown that $P(k+1)$ is true under this assumption, that is, that $k+1$ is the product of primes. 

There are two cases to consider, when $k+1$ is prime and when $k+1$ is composite. If $k+1$ is prime, we immediately see that $P(k+1)$ is true. Otherwise, $k+1$ is composite and can be written as the product of two positive integers $a$ and $b$ with $2 \leq a \leq b<k+1$. Because both $a$ and $b$ are integers at least $2$ and not exceeding $k$, we can use the inductive hypothesis to write both $a$ and $b$ as the product of primes. Thus, if $k+1$ is composite, it can be written as the product of primes, namely, those primes in the factorization of $a$ and thoser in the factorization of $b$. 


## Proof of division algorithm
**Theorem:** For all natural numbers $n$ and $m$, if $m \gt 0$, then there are natural numbers $q$ and $r$ such that $n=mq+r$ and $r \lt m$ (the numbers $q$ and $r$ are called the quotient and remainder when $n$ is divided by $m$).

**Scratch Work:** We let $m$ be an arbitrary positive integer and then we use strong induction to prove that $\forall n \exists q \exists r(n=m q+r \wedge r<m)$ (for all $n \in \natnums$ there exists a $q$ and $r$ where $n$ is equal to $mq+r$ and $r$ is less than $m$. According to strong induction, this means we should let $n$ be an arbitrary natural number, assume that $\forall k<n \exists q \exists r(k=m q+r \wedge r<m)$ ( $P(n)$ is true for all $n \le k$) and prove that $\exists q \exists r(n=m q+r \wedge r<m)$.

The goal is an existential statement so we need to come up with values of $q$ and $r$ with the required properties. 

If $n \lt m$ we can just let $q=0$ and $r=n$ (multiply a number by 0 and add the number to the product to get...itself).

If $n \ge m$, this won't work, since we must have $m \gt r$, so we must do something different. The inductive hypothesis starts with $\forall k \lt n$, so to apply it we should plug in some nat num smaller than $n$ for $k$, but what should we plug in?? If we think of division as repeated subtraction, then dividing $n$ by $m$ invovles subtracting $m$ from $n$ repeatedly. The first step would be to compute $n-m$, which is a natural number smaller than $n$. Perhaps we should plug in $n-m$ for $k$. Note that we are using the fact that a quotient and remainder exist for some nat number smaller than $n$ to prove they exist for $n$, but this smaller number is not $n-1$ its $n-m$. **This is why we need strong induction**.

**Proof:**
We let $m$ be an arbitrary positive integer and then proceed by strong induction on $n$. 
Suppose $n \in \natnums$, and for every $k \lt n$ there are natural numbers $q$ and $r$ such that $k=m q+r$ and $m \gt r$.

We proceed by cases. 

*Case 1:* $n \lt m$. Let $q=0$ and $r=n$. Then clearly $n=m q+r$ and $r \lt m$.
*Case 2:* $n \ge m$. Let $k=n-m \lt n$ and note that since $n \ge m$, $k$ is a natural number. By inductive hypothesis, we can choose $q^{\prime}$ and $r^{\prime}$ such that $k=m q^{\prime}+r^{\prime}$ and $r^{\prime}<m$. Then $n-m=m q^{\prime}+r^{\prime}$, so $n=m q^{\prime}+r^{\prime}+m=m\left(q^{\prime}+1\right)+r^{\prime}$. Thus, if we let $q=q^{\prime}+1$ and $r=r^{\prime}$, then we have $n=mq+r$ and $r \lt m$, as required. $\blacksquare$.

## Proof of formula for fibonacci numbers
**Theorem:** If $F_n$ is the $n^{th}$ Fibonacci number, then 

$$
F_{n}=\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{n}-\left(\frac{1-\sqrt{5}}{2}\right)^{n}}{\sqrt{5}}
$$

**Scratch:** Because $F_0$ and $F_1$ are defined separately from $F_n$ for $n \ge 2$, we check the formula for these cases separately. For $n \ge 2$, the definition of $F_n$ suggests that we should use the assumption that the formula is correct for $F_{n-2}$ and $F_{n-1}$ to prove it is correct for $F_n$. **Because we need to know that the formula works for the two previous cases, we must use strong induction rather than regular induction.** 

**Proof:** We use strong induction. Let $n$ be an arbitrary natural number, and suppose that for all $k \lt n$, 

$$
F_{k}=\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{k}-\left(\frac{1-\sqrt{5}}{2}\right)^{k}}{\sqrt{5}}
$$

We proceed by cases.

**Case 1:** $n=0$. Then, 

$$
\begin{aligned}
\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{n}-\left(\frac{1-\sqrt{5}}{2}\right)^{n}}{\sqrt{5}} &=\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{0}-\left(\frac{1-\sqrt{5}}{2}\right)^{0}}{\sqrt{5}} \\
&=\frac{1-1}{\sqrt{5}}=0=F_{0}
\end{aligned}
$$

**Case 2:** $n=1$. Then, 

$$
\begin{aligned}
\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{n}-\left(\frac{1-\sqrt{5}}{2}\right)^{n}}{\sqrt{5}} &=\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{1}-\left(\frac{1-\sqrt{5}}{2}\right)^{1}}{\sqrt{5}} \\
&=\frac{\sqrt{5}}{\sqrt{5}}=1=F_{1}
\end{aligned}
$$

**Case 3:** $n \ge 2$. Applying the inductive hypothesis to $n-2$ and $n-1$, we get

$$
\begin{aligned}
F_{n} &=F_{n-2}+F_{n-1} \\
&=\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{n-2}-\left(\frac{1-\sqrt{5}}{2}\right)^{n-2}}{\sqrt{5}}+\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{n-1}-\left(\frac{1-\sqrt{5}}{2}\right)^{n-1}}{\sqrt{5}} \\
&=\frac{\left[\left(\frac{1+\sqrt{5}}{2}\right)^{n-2}+\left(\frac{1+\sqrt{5}}{2}\right)^{n-1}\right]-\left[\left(\frac{1-\sqrt{5}}{2}\right)^{n-2}+\left(\frac{1-\sqrt{5}}{2}\right)^{n-1}\right]}{\sqrt{5}} \\
&=\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{n-2}\left[1+\frac{1+\sqrt{5}}{2}\right]-\left(\frac{1-\sqrt{5}}{2}\right)^{n-2}\left[1+\frac{1-\sqrt{5}}{2}\right]}{\sqrt{5}} .
\end{aligned}
$$

Now we note that 

$$
\left(\frac{1+\sqrt{5}}{2}\right)^{2}=\frac{1+2 \sqrt{5}+5}{4}=\frac{6+2 \sqrt{5}}{4}=\frac{3+\sqrt{5}}{2}=1+\frac{1+\sqrt{5}}{2}
$$

and similarly 

$$
\left(\frac{1-\sqrt{5}}{2}\right)^{2}=1+\frac{1-\sqrt{5}}{2}
$$

Substituting into the formula for $F_n$, we get 
$$
\begin{aligned}
F_{n} &=\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{n-2}\left(\frac{1+\sqrt{5}}{2}\right)^{2}-\left(\frac{1-\sqrt{5}}{2}\right)^{n-2}\left(\frac{1-\sqrt{5}}{2}\right)^{2}}{\sqrt{5}} \\
&=\frac{\left(\frac{1+\sqrt{5}}{2}\right)^{n}-\left(\frac{1-\sqrt{5}}{2}\right)^{n}}{\sqrt{5}}  
\end{aligned}
$$

$$
\hspace{32em} \blacksquare
$$