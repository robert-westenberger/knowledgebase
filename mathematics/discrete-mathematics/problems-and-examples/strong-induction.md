---
title: Strong Induction Exercises
description: 
published: true
date: 2021-04-25T00:24:56.916Z
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
**c)** In the inductive step we need to prove $P(k) \rarr P(k+1)$ assuming $P(k)$ is true for $k \ge 8$.
**d)** We assume $P(k)$, that a postage of $k$ cents can be formed from $3$ and $5$ cent stamps. Since $k \ge 10$, we can know that $P(k-2)$ is true, that we can form $k-2$ cents of postage. Put another $3$ cent stamp on the envelope, and we have formed $k+1$ cents of postage.
**e)** We have completed both the basis and inductive steps, so by the principal of strong induction, the statement is true for every integer $n \ge 8$.

## 5
**a)** Determine which amounts of postage can be formed using just 4-cent and 11-cent stamps. 
**b)** Prove your answer to (a) using the principle of mathematical induction. Be sure to state explicitly your inductive hypothesis in the inductive step. 
**c)** Prove your answer to (a) using strong induction. How does the inductive hypothesis in this proof differ from that in the inductive hypothesis for a proof using mathematical induction?
### Solution
**a)** Adding together by hand we can form 4, 8, 11, 12, 15, 16, 19, 20, 22, 23, 24, 26, 27, 28, 30, 31, 32, 33. For any postage $n \ge 30$, it can be formed from just $4$ and $11$ cent stamps. 
**b)** The inductive hypothesis is $P(k)$ is true. We want to prove it for $k \ge 30$. We want to show that, assuming $P(k)$, that $P(k) \rarr P(k+1)$. We consider two cases. For the first case, if the $k$ cents includes an $11$ cent stamp, replace it with $3$ $4$ cent stamps ($4+4+4=11 + 1$).
**c)**