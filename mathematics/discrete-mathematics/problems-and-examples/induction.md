---
title: Induction Exercises
description: 
published: true
date: 2021-04-14T19:11:10.674Z
tags: discrete-mathematics
editor: markdown
---

# Rosen Discrete Mathematics 7th Edition Section 


### 1
There are infinitely many stations on a train route. Suppose
that the train stops at the first station and suppose
that if the train stops at a station, then it stops at the next
station. Show that the train stops at all stations.
#### Solution
Let $P(n)$ be the statement that the train stops at station $n$. We want to prove that $P(n)$ is true for all positive integers $n$. For the basis step, we are told that $P(1)$ is true. For the inductive step, we are told that $P(k)$ implies $P(k+1)$ for each $k \ge 1$. Therefore by the principle of mathematical induction, $P(n)$ is true for all positive integers $n$.

### 3 
Let $P(n)$ be the statement that $1^{2}+2^{2}+\cdots+n^{2}=n(n+\text { 1) }(2 n+1) / 6$  for the positive integer $n$. 
**a)** What is the statement $P(1)$?
**b)** Show that $P(1)$ is true, completing the basis step of a proof that $P(n)$ is true for all positive integers $n$.
**c)** What is the inductive hypothesis of a proof that $P(n)$ is true for all positive integers $n$?
**d)** What do you need to prove in the inductive step of a proof that $P(n)$ is true for all positive integers $n$?
**e)** Complete the inductive step of a proof that $P(n)$ is true for all positive integers $n$, identifying where you use the inductive hypothesis. 
**f)** Explain why these steps show that this formula is true whenever $n$ is a positive integer.
#### Solution
**a)** $P(1)=1^2 =1^2=1(1+1)(2+1) / 6$
**b)** $P(1)=1^2=1(1+1)(2+1) / 6 =1(2)(3)/6=1$
**c)** That $P(k)$ is true for all arbitrary integer $k$, that is
$$
1^{2}+2^{2}+\cdots+k^{2}=\frac{k(k+1)(2 k+1)}{6}
$$
**d)** We want to show that  for each $k \ge 1$ that $P(k)$ implies $P(k+1)$.
In other words, we want to show that assuming the inductive hypothesis (part C) that we can show 
$$
\begin{aligned}
1^{2}+2^{2}+\cdots+k^{2}+(k+1)^{2} & = \frac{k(k+1)(2 k+1)}{6}+(k+1)^{2} \\
&= \frac{k(k+1)(2 k+1)+6(k+1)^{2}}{6} \\
&= \frac{(k+1)[k(2 k+1)+6(k+1)]}{6} \\
&= \frac{(k+1)\left(2 k^{2}+7 k+6\right)}{6} \\
&= \frac{(k+1)(k+2)(2 k+3)}{6}
\end{aligned}
$$
**e)** The left hand side of part **d** shows $k(k+1)(2 k+1) / 6+ (k+1)^{2}$. We need to do a bit of algebraic manipulation to get it into the desired form: factor out $(k+1)/6$ and then factor the rest. 
**f)** Explain why these steps show that this formula is true whenever n is a positive integer.

$$
\begin{aligned}
\left(1^{2}+2^{2}+\cdots+k^{2}\right)+(k+1)^{2}&=\frac{k(k+1)(2 k+1)}{6}+(k+1)^{2} \\
&=\frac{k+1}{6}(k(2 k+1)+6(k+1))\\
&=\frac{k+1}{6}\left(2 k^{2}+7 k+6\right) \\
&=\frac{k+1}{6}(k+2)(2 k+3) \\
&=\frac{(k+1)(k+2)(2 k+3)}{6}
\end{aligned}
$$