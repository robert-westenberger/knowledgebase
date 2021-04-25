---
title: Strong Induction + More Well Ordering Principle Exercises
description: 
published: true
date: 2021-04-25T02:23:18.449Z
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
**b)** The inductive hypothesis is $P(k)$ is true. We want to prove it for $k \ge 30$. We want to show that, assuming $P(k)$, that $P(k) \rarr P(k+1)$. We consider two cases. For the first case, if the $k$ cents includes an $11$ cent stamp, replace it with $3$ $4$ cent stamps ($4+4+4=11 + 1$). Otherwise, $k$ includes no $11$ cent stamps and has been formed from just $4$ cent stamps. Because $k \ge 30$, that means that at least eight $4$ cent stamps were used. Replace those eight $4$ cent stamps with three $11$ cent stamps, and we have formed $k+1$ cents in postage ($3 \cdot 11=8\cdot4+1$).
**c)** $P(k)$ is the same as in part b. This time for our strong induction basis step, we see $P(k)$ is true for $k=30,31,32,33$. Assuming that $P(j)$ is true for all $j$ with $30 \le j \le k$, where $k \ge 33$, we want to show that $P(k+1)$ is true. $k-1 \ge 30$, we know that $P(k-3)$ is true. Put one more $4$ cent stamp in the envelope, and we have $k+1$ cents of postage as desired. 
## 9
Use strong induction to prove that $\sqrt 2$ is irrational. (Hint: Let $P(n)$ be the statement that $\sqrt2 \ne \frac nb$ for any positive integer $b$).
### Solution
$P(n)= \neg \exists b (b \in \Z \wedge b \gt 0 \wedge \frac nb = \sqrt 2 )$ ("there is no positive integer $b$ such that $n/b = \sqrt 2$. $P(1)$ is true because $\sqrt{2}>1 \geq 1 / b$ for all positive integers $b$. For the inductive step, we assume $P(j)$ is true for all $j \le k$, where $k$ is an arbitrary positive integer; we must prove $P(k+1)$ is true. 

Assuming the contrary, that $\sqrt{2}=(k+1) / b$ for some $b$. Squaring both sides and clearing fractions we get $2b^2 =(k+1)^2$. This tells us that $(k+1)^2$ is even, and so $k+1$ is as well (the square of an even number is always even). Therefore we can write $k+1=x$ for some positive integer $x$. Substituting, we have $2 b^{2}=4 x^{2}$, so $b^{2}=2 x^{2}$. We see that $b$ is even, so $b=2y$ for some positive integer $y$. then we have $\sqrt{2}=(k+1) / b=(2x) /(2 y)=x / y$. But $x \lt k$,so this contradicts the inductive hypothesis, and our proof of the inductive step is complete.


## 13
A jigsaw puzzle is put together by successively joining pieces that fit together into blocks. A move is made each time a piece is added to a block, or when two blocks are joined. Use strong induction to prove that no matter how the moves are carried out, exactly $n − 1$ moves are required to assemble a puzzle with $n$ pieces.
### Solution
$P(n)=n-1 \medspace \text {moves are required to assemble a puzzle with} \medspace n \medspace \text {pieces}$.

**Base Case:** $P(1)$ is trivially true. 
**Inductive Hypothesis:** $P(j)$ is true for all $j \lt n$.
**Inductive Step:** Consider a puzzle with $n$ pieces. The final move must be the joining of two blocks $k$ and $n-k$ for some integer $k$, $1 \le k \le n-1$. By the inductive hypothesis, it required $k-1$ moves to construct the one block, and $n-k-1$ moves to construct the other. Therefore, $1+(k-1)+(n-k-1)=n-1$ moves are required in all, so $P(n)$ is true. We have proved that $P(n)$ under the assumption that $P(j)$ was true for $j \lt n$.

# Unsourced
## 1 
Use the well ordering principle to prove that there is no solution over the positive integers to the equation
$$4 a^{3}+2 b^{3}=c^{3}$$
### Solution

$P(a, b, c)$ is the statement that there is no solution to $4 a^{3}+2 b^{3}=c^{3}$ for $a \gt 0$, $b \gt 0$, $c \gt 0$.
$X$ is the set of counterexamples of $P$:
$X::=\{a \in \mathbb{N} \wedge b \in \mathbb{N} \wedge c \in \mathbb{N}  \mid \neg(P(n))\}$

Assume for proof by contradiction that $X$ is nonempty. That is, $X$ contains contains values that make $4 a^{3}+2 b^{3}=c^{3}$ true. By the WOP, there must be an $c \in X$ that is the smallest value that makes the equation true.