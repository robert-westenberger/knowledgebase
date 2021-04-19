---
title: Induction Exercises
description: 
published: true
date: 2021-04-19T00:10:45.106Z
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
$$
\begin{aligned}
\left(1^{2}+2^{2}+\cdots+k^{2}\right)+(k+1)^{2}&=\frac{k(k+1)(2 k+1)}{6}+(k+1)^{2} \\
&=\frac{k+1}{6}(k(2 k+1)+6(k+1))\\
&=\frac{k+1}{6}\left(2 k^{2}+7 k+6\right) \\
&=\frac{k+1}{6}(k+2)(2 k+3) \\
&=\frac{(k+1)(k+2)(2 k+3)}{6}
\end{aligned}
$$
**f)** We have completed both the basis step and the inductive step, so by the principle of mathematical induction, the statement is true for every positive integer $n$.
### 7
Prove that $3+3 \cdot 5+3 \cdot 5^{2}+\cdots+3 \cdot 5^{n}=3\left(5^{n+1}-1\right) / 4$ whenever $n$ is a nonnegative integer.
#### Solution
**Theorem:** For all $n \in \natnums$, $3+3 \cdot 5+3 \cdot 5^{2}+\cdots+3 \cdot 5^{n}= \frac{3\left(5^{n+1}-1\right)} 4$.
**Proof:**
**Base Case:** 
$$
\begin{aligned}
P(0) &= \frac{3\left(5^{0+1}-1\right)} 4 \\
&= \frac{3\left(5^1-1\right)} 4 \\
&= \frac{3\left(5-1\right)} 4 \\
&= \frac{3\left(4\right)} 4 \\
&= \frac{12} 4 \\
&= 3
\end{aligned}
$$

**Induction Hypothesis:** $P(k)$ implies $P(k+1)$ where $P(k)=3+3 \cdot 5+3 \cdot 5^{2}+\cdots+3 \cdot 5^{k}= \frac{3\left(5^{k+1}-1\right)} 4$ and $P(k+1)=3+3 \cdot 5+3 \cdot 5^{2}+\cdots+3 \cdot 5^{(k+1)}= \frac{3\left(5^{(k+2)}-1\right)} 4$.

**Induction Case:**
$$
\begin{aligned}
3+3 \cdot 5+3 \cdot 5^{2}+\cdots+3 \cdot 5^{k} + 5^{k+1} &= \frac{3\left(5^{k+1}-1\right)} 4 + 3 \cdot 5^{k+1} \\[1em]
&=5^{k+1}\left(\frac{3}{4}+3\right)-\frac{3}{4} \\[1em]
&= 5^{k+1} \cdot \frac{15}{4}-\frac{3}{4} \\[1em]
&= \frac{3\left(5^{(k+2)}-1\right)} 4 \\[1em]
&= 5^{k+2} \cdot \frac{3}{4}-\frac{3}{4} \\[1em]
&=\frac{3\left(5^{k+2}-1\right)}{4}
\end{aligned}
$$


### 9
**a)** Find a formula for the sum of the first $n$ even positive
integers.
**b)** Prove the formula that you conjectured in part **(a)**.
#### Solution
**a)** $2+4+6+8+...+n=n(n+1)$
**b)**
Proof by induction. 
**Base Case:** $P(1)= 1(2) = 2$
**Induction Hypothesis:** $P(k)$ implies $P(k+1)$ where $P(k)=2+4+6+8+...+k=k(k+1)$ and $P(k+1)=2+4+6+8+...+(k+1)=(k+1)(k+2)$.
**Induction Step:** 
$$
\begin{aligned}
2+4+6+8+...+ k + (k+1) &= k(k+1) + (k+1) \\
&= k^2 + k + k + 1 \\
&= k^2 + 2k + 1 + k + 1\\
&= k^2 + 3k + 2\\
&= (k+1)(k+2)
\end{aligned}
$$

This shows that $P(k+1)$ follows from $P(k)$. 
### 11 
**a)** Find a formula for 
$$
\frac{1}{2}+\frac{1}{4}+\frac{1}{8}+\cdots+\frac{1}{2^{n}}
$$
by examining the values of this expression for small values of $n$.
**b)** Prove the formula you conjectured in part (a).

#### Solution
**a)** $\frac{1}{2}+\frac{1}{4}+\cdots+\frac{1}{2^{n}}=\frac{2^n - 1}{2^n}$.
**b)** Proof by induction. 
**Base Case:** $P(1)= \frac {1}{2}=\frac{2^1 - 1}{2^1}=\frac{1}{2}$.
**Induction Hypothesis:** $P(k)$ implies $P(k+1)$ where $P(k)=\frac{1}{2}+\frac{1}{4}+\cdots+\frac{1}{2^{k}}=\frac{2^k - 1}{2^k}$ and $P(k+1)=\frac{1}{2}+\frac{1}{4}+\cdots+\frac{1}{2^{(k+1)}}=\frac{2^{(k+1)} - 1}{2^{(k+1)}}$.

**Induction Step:** 
$$
\begin{aligned}
\frac{1}{2}+\frac{1}{4}+\cdots+\frac{1}{2^{k}} + \frac{1}{2^{(k+1)}} &=\frac{2^k - 1}{2^k} +  \frac{1}{2^{(k+1)}} \\
&=\frac{2 \cdot 2^{k}-2 \cdot 1+1}{2^{k+1}}\\
&= \frac{2^{(k+1)} - 1}{2^{(k+1)}}
\end{aligned}
$$

### 19
Let $P(n)$ be the statement that 
$$1+\frac{1}{4}+\frac{1}{9}+\cdots+\frac{1}{n^{2}}<2-\frac{1}{n}$$
where $n$ is an integer and greater than $1$.
**a)** What is the statement $P(2)$?
**b)** Show that $P(2)$ is true, completing the basis step of
the proof.
**c)** What is the inductive hypothesis?
**d)** What do you need to prove in the inductive step?
**e)** Complete the inductive step.
**f)** Explain why these steps show that this inequality is
true whenever n is an integer greater than 1.
#### Solution
**a)** $P(2)=1+\frac{1}{4}<2-\frac{1}{2}$
**b)** $P(2)=\frac{5}{4}<\frac{6}{4}$. This is true because $\frac 5 4$ is less than $\frac 6 4$.
**c)** Inductive hypothesis is $P(k)$ which is the mathematical statement that $1+\frac{1}{4}+\frac{1}{9}+\cdots+\frac{1}{k^{2}}<2-\frac{1}{k}$
**d)** That $P(k) \rarr P(k+1)$ where $P(k+1)$ is the mathematical statement $1+\frac{1}{4}+\frac{1}{9}+\cdots+\frac{1}{(k+1)^{2}}\lt2-\frac{1}{(k+1)}$ for $k \ge 2$. 
**e)**

$$
\begin{aligned}
1+\frac{1}{4}+\cdots+\frac{1}{k^{2}}+\frac{1}{(k+1)^{2}} &<2-\frac{1}{k}+\frac{1}{(k+1)^{2}} \\
&=2-\left(\frac{1}{k}-\frac{1}{(k+1)^{2}}\right) \\
&=2-\left(\frac{k^{2}+2 k+1-k}{k(k+1)^{2}}\right) \\
&=2-\frac{k^{2}+k}{k(k+1)^{2}}-\frac{1}{k(k+1)^{2}} \\
&=2-\frac{1}{k+1}-\frac{1}{k(k+1)^{2}}<2-\frac{1}{k+1}
\end{aligned}
$$
Above.. 
1) Assume inductive hypothesis. Add $\frac 1 {(k+1)^2}$ to both sides of the inequality.
2) 
**f)** We've completed the basis and inductive step, so by the prinicipal of mathematical induction, the statement is true for every positive integer $n \gt 1$.

### 21 
Prove that $2^n \gt n^2$ if $n \in \Z$ and $n \gt 4$.
#### Solution
Proof by induction.
**Base Case:** $P(5) =2^5 \gt 5^2 = 32 \gt 25$
# Random / Unsourced
## Proof by Induction
Prove by induction that $11^n - 6$ is divisible by $5$ for every positive integer $n$. 

Let $P(n)$ by the mathematical statement 
$$
11^{n}-6 \text { is divisible by } 5 \text { . }
$$

**Base Case:** $P(1)=11^1-6=5$ which is divisible by $5$ so $P(1)$ is true.
**Induction Hypothesis:** Assume that $P(k)$ is correct for some positive integer $k$. That means $11^k − 6$ is divisible by $5$ and hence $11^k − 6 = 5m$ for some integer $m$. So $11^k = 5m + 6$.

**Induction Step:** We want to show that $11^{k+1} - 6$ can be expressed as a multiple of $5$, so we will start with the formula $11^{k+1} - 6$ and we will rearrange it into something involving multiples of $5$. At some point we will also want to use the assumption that $11^k=5m+6$.

$$
\begin{aligned}
11^{k+1}-6&=\left(11 \times 11^{k}\right)-6 \quad \text {by the laws of powers} \\
&=11(5m+6)-6 \quad \text {by the induction hypothesis} \\
&=11(5m)+66-6 \quad \text {by expanding the bracket} \\
&=5(11m)+60 \\ 
&=5(11m+12) \quad \text {since both parts of the formula have a common factor of} \medspace 5
\end{aligned}
$$
As $11m + 12$ is an integer we have that $11^{k+1} − 6$ is divisible by $5$, so $P(k + 1)$ is correct. Hence by mathematical induction $P(n)$ is correct for all positive integers $n$.

## Proof by Induction (Involving Inequality)
Prove by induction that $2^{n} \gt 2 n$ for every positive integer $n \gt 2$

**Base Case**: $P(3)$ = $2^3 \gt 2(3) = 8 \gt 6$
**Induction Hypothesis:** Assume that $P(k)$ is correct for some positive integer $k \gt 3$. That means $2^{k} \gt 2 k$.
**Induction Step:** We want to show that $2^{k+1} \gt 2(k+1)$. 

$$
\begin{aligned}
2^{k}>2 k & \Longrightarrow 2^{k+1}>2 \times 2 k \\
& \Longrightarrow 2^{k+1}>2 k+2 k \\
& \Longrightarrow 2^{k+1}>2 k+2 \\
& \Longrightarrow 2^{k+1}>2(k+1)
\end{aligned}
$$
So $P(k+1)$ is correct. Hence by mathematical induction $P(n)$ is correct for all positive integers $n \gt 2$.

## Proof by Induction (Involving Inequality)
**Theorem:** For every natural number $n \ge 5$, $2^n \gt n^2$. 
**Proof:** By mathemtical induction.

**Base case:** When $n=5$ we have $2^n=32 \gt 25 = n^2$

**Induction Hypothesis:** $P(k)$ implies $P(k+1)$ where $P(k+1)$ is $2^{k+1} \gt (k+1)^2$.

**Induction Step:**
$$
\begin{aligned}
2^{k+1} &=2 \times 2^k \\ 
&\gt 2 \times k^2 \\
&=k^2 + k^2 \\
&\ge k^2 + 5k \quad \text {(since} \medspace k \ge 5 \text{)} \\
&=k^{2}+2 k+3 k \\
& \gt k^{2}+2 k+1=(k+1)^{2}
\end{aligned}
$$


## Proof by Induction (Involving summation)
**Theorem:** For all $n \in \mathbb{N}, 0^{3}+1^{3}+2^{3}+\cdots+n^{3}=\lbrack n(n+1) / 2\rbrack^{2}$.
**Proof:**
**Base Case:** $P(0) = 0^3 = \left(0 \times \frac{0+1}{2}\right)^{2} = 0$
**Inductive Hypothesis:** $P(k)$ implies $P(k+1)$ where $P(k)=0^{3}+1^{3}+2^{3}+\cdots+k^{3}=\lbrack k(k+1) / 2\rbrack^{2}$ and $P(k+1)$ = $0^{3}+1^{3}+2^{3}+\cdots(k+1)^{3}=\lbrack (k+1)((k+1)+1) / 2\rbrack^{2}=\lbrack (k+1)((k+2) / 2\rbrack^{2}$.
**Inductive Step:** 
$$
\begin{aligned}
1^{3}+2^{3}+3^{3}+\cdots+k^{3}+(k+1)^{3} &=\frac{k^{2}(k+1)^{2}}{4}+(k+1)^{3} \\
&=\frac{k^{2}(k+1)^{2}+4(k+1)^{3}}{4} \\
&=\frac{(k+1)^{2}\left(k^{2}+4 k+4\right)}{4} \\
&=\frac{(k+1)^{2}(k+2)^{2}}{4} \\
1^{3}+2^{3}+3^{3}+\cdots+k^{3}+(k+1)^{3} &=\frac{(k+1)^{2}(k+2)^{2}}{4}
\end{aligned}
$$

## Proof by Induction (Involving summation)
**Theorem:** For all $n \in \natnums$, $0 \cdot 1+1 \cdot 2+2 \cdot 3+\cdots+n(n+1)=\frac{n(n+1)(n+2)} 3$.
**Proof:** 
**Base Case:** $P(0) = 0(0+1) = \frac{0(0+1)(0+2)} 3 = 0$.
**Inductive Hypothesis:** $P(k)$ implies $P(k+1)$ where $P(k)=0 \cdot 1+1 \cdot 2+2 \cdot 3+\cdots+k(k+1)=\frac{k(k+1)(k+2)} 3$ and $P(k+1)=0 \cdot 1+1 \cdot 2+2 \cdot 3+\cdots+(k+1)(k+2)=\frac{(k+1)((k+1)+1)((k+1)+2)} 3 =\frac{(k+1)(k+2)(k+3)} 3$.
**Inductive Step:**
$$
\begin{aligned}
0 \cdot 1+1 \cdot 2+2 \cdot 3+\cdots+k(k+1) + (k+1)(k+2)&=\frac{k(k+1)(k+2)} 3 + (k+1)(k+2)\\
&= \frac{k(k+1)(k+2)} 3 + \frac{3(k+1)(k+2)} 3 \\
&= \frac{k(k+1)(k+2) + 3(k+1)(k+2)} 3 \\
&= \frac{(k+1)(k+2)(k+3)} 3 \quad \text{factor out } \medspace (k+1)(k+2)
\end{aligned}
$$