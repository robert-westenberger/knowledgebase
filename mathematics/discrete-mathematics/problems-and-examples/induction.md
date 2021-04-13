---
title: Induction Exercises
description: 
published: true
date: 2021-04-13T19:15:40.082Z
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