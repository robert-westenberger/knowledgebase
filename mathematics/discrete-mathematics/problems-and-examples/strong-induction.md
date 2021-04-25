---
title: Strong Induction + More Well Ordering Principle Exercises
description: 
published: true
date: 2021-04-25T23:43:25.023Z
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

## 29
What is wrong with this “proof” by strong induction?
“Theorem” For every nonnegative integer $n$, $5n = 0$.
**Basis Step:** $5 \cdot 0 = 0$.
**Inductive Step:** Suppose that $5j = 0$ for all nonnegative
integers $j$ with $0 \le j \le k$. Write $k + 1 = i + j$ ,
where $i$ and $j$ are natural numbers less than $k + 1$. By the
inductive hypothesis, $5(k + 1) = 5(i + j) = 5i + 5j =
0 + 0 = 0$.

### Soln
The error is going from the basis step $n=0$ to the next value $n=1$. We can't write $1$ as the sum of two smaller natural numbers, so we can't invoke the inductive hypothesis. In the notation of the "proof", when $k=0$, we cannot write $0+1=i+j$ where $0 \le i \le 0$ and $0 \le j \le 0$.

## 30
Find the flaw with the following “proof” that $a^n = 1$ for
all nonnegative integers $n$, whenever $a$ is a nonzero real
number.
**Basis Step:** $a^0 = 1$ is true by the definition of $a^0$.
**Inductive Step:** Assume that $a^j = 1$ for all nonnegative
integers $j$ with $j \le k$. Then note that
$$
a^{k+1}=\frac{a^{k} \cdot a^{k}}{a^{k-1}}=\frac{1 \cdot 1}{1}=1
$$
### Solution
The denominator contains $a^{k-1}$ (which is $a^k$, for which we have proved nothing). Our inductive step requires $k \ge 1$.. but we want to start induction at $k=0$. 
## 41
Show that the well-ordering property can be proved when the principle of mathematical induction is taken as an axiom.
### Solution
We will prove this by contradiction. Suppose that the well-ordering property were false. Let $S$ b e a counterexample: a nonempty set of nonnegative integers that contains no smallest element. Let $P(n)$ be the statement "$i \notin S$ for all $i \leq n$". We will show that $P(n)$ is true for all $n$ (which will contradict the assertion that $S$ is nonempty). Now $P(0)$ must be true, because if $0 \in S$ then clearly $S$ would have a smallest element, namely $0$. Suppose now that $P(n)$ is true, so that $i \notin S$. If $n+1 \in S$, then $n+1$ would be the smallest element of $S$, and this would contradict our assumption. Therefore $n+1 \notin S$. Thus we have shown by the principle of mathematical induction that $P(n)$ is true for all $n$, which means there can be no elements of $S$. This contradiction our assumption that $S \ne \emptyset$, and our proof by contradiction is complete. 
# Unsourced
## 1 
Use the well ordering principle to prove that there is no solution over the positive integers to the equation
$$4 a^{3}+2 b^{3}=c^{3}$$
### Solution

$P(a, b, c)$ is the statement that there is no solution to $4 a^{3}+2 b^{3}=c^{3}$ for $a \gt 0$, $b \gt 0$, $c \gt 0$.
$X$ is the set of counterexamples of $P$:
$X::=\{a \in \mathbb{N} \wedge b \in \mathbb{N} \wedge c \in \mathbb{N}  \mid \neg(P(n))\}$

Assume for proof by contradiction that $X$ is nonempty. That is, $X$ contains contains values that make $4 a^{3}+2 b^{3}=c^{3}$ true. By the WOP, there must be an $a \in X$ that is the smallest value that makes the equation true. We see that the left hand side of the equation is even, so $c$ must be even. So $c=2t$ for some integer $t$. Substituting that in we get..

$$
\begin{aligned}
4 a^{3}+2 b^{3}&=(2t)^{3} \\
4 a^{3}+2 b^{3}&=8t^{3} \\
2 a^{3}+b^{3}&=4t^{3} \quad \text {divide both sides by 2}\\
\end{aligned}
$$

We see $b^3$ is even, so $b$ must also be even. There must be some positive integer $y$ where $b=2y$. Substituting again we get

$$
\begin{aligned}
2 a^{3}+(2y)^{3}&=4t^{3} \\
2 a^{3}+8y^{3}&=4t^{3} \\
a^{3}+4y^{3}&=2t^{3} \quad \text {divide both sides by 2}\\
\end{aligned}
$$

We see that $a^3$ is even, so $a$ must be even. There must be an integer $d$ where $a=2d$. Substituting once more we get 

$$
\begin{aligned}
(2d)^{3}+4y^{3}&=2t^{3} \\
8d^{3}+4y^{3}&=2t^{3} \\
4d^{3}+2y^{3}&=t^{3} \quad \text {divide both sides by 2} \\
\end{aligned}
$$

We see that $a=d$, $b=y$, and $c=t$. This appears to be another solution to the original equation, so $d$, $y$, and $t$ are elements of $X$. This is a contradiction though, because $d \lt a$ and $a$ was defined as being the smallest value that makes the equation true (the smallest value in $X$). 
