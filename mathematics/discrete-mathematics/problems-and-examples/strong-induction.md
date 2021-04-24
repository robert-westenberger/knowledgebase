---
title: Strong Induction Exercises
description: 
published: true
date: 2021-04-24T23:54:50.685Z
tags: discrete-mathematics
editor: markdown
---

# Rosen Discrete Mathematics 7th Edition Section 5.2


## 1
Use strong induction to show that if you can run one mile or two miles, and if you can always run two more miles once you have run a specified number of miles, then you can run any number of miles.

### Solution
Let $P(n)$ be the statement that you can run $n$ miles. We want to prove $P(n)$ is true for all positive integers $n$. 

**Basis Step:** $P(1)$ and $P(2)$ are true. 

**Inductive Step:** Fix $k \ge 2$ and assume $P(j)$ is true for all $j \le k$. We want to show $P(k+1)$ is true. Since $k \ge 2$, $k-1$ is a positive integer less than or equal to $k$. By the inductive hypothesis, we know that $P(k-1)$ is true. That is, we know that  you can run $k-1$ miles. Since "you can always run two more miles once you have run a specified number of miles", we know that you can run $(k-1)+2=k+1$ miles. This is $P(k+1)$.

## 3
Let $P(n)$ be the statement that a postage of $n$ cents can be formed using just 3-cent stamps and 5-cent stamps. The parts of this exercise outline a strong induction proof that $P(n)$ is true for $n \ge 8$.
**a)** Show that the statements $P(8)$, $P(9)$, and $P(10)$ are
true, completing the basis step of the proof.
**b)** What is the inductive hypothesis of the proof?
**c)** What do you need to prove in the inductive step?
**d)** Complete the inductive step for $k \ge 10$.
**e)** Explain why these steps show that this statement is
true whenever $n \ge 8$.
### Solution
**a)**$P(8)=3 + 5$, $P(9)=3+3+3$, $P(10)=5+5$
**b)** Inductive hypothesis is the statement that $P(k)$ is true, that is, a postage of $k$ cents can be formed from $3$ and $5$ cent stamps. 
**c)**
**d)**
**e)**