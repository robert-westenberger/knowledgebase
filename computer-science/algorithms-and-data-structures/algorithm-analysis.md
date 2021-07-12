---
title: Algorithm Analysis
description: 
published: true
date: 2021-07-12T00:34:55.122Z
tags: data-structures, algorithms
editor: markdown
---

# The RAM Model of Computation
Machine-independent algorithm design depends upon a hypothetical computer called the Random Access Machine (RAM). This hypothetical computer has the following attributes:
* Each simple operation (+, *, -, =, if, call) takes exactly one time step.
* Loops and subroutines are a composition of many single-step operations. The time it takes to run through a loop or execute a subprogram depends on the number of loop iterations or the specific nature of the subprogram.
* Each memory access takes one time step. The RAM has unlimited memory.

Run time on the RAM is measured by counting the number of steps an algorithm takes on a given problem instance.

## Best-Case, Worst-Case, and Average-Case Complexity
" "-Case refers to the resources (computations, memory) required for an algorithm to finish.

* **Best-case** - Minimum number of steps taken in any instance of size $n$.
* **Average-case** - Average number of steps over all instances of size $n$. Average-case is useful for randomized algorithms.
* **Worst-case** - Maximum number of steps taken in any instance of size $n$. This is typically the most important / useful case to observe.  

Each time complexity defines a numerical function for any given algorithm. These functions are as well defined as any other numberical function. 
### Example - Sorting algorithm
The best case for a sorting algorithm would be an empty array, or an array that is already in order.
The worse case would be an array that is in the opposite preferred sort order.
## Big O Notation
The Big O simplifies analysis of algorithms by ignoring levels of detail that don't impact comparison between algorithms. For example, difference between multiplicative constants. $f(n)=2 n$ and $g(n)=n$ are identical in Big O analysis

![asymptotic-notation-graphs.png](/asymptotic-notation-graphs.png)
**(a)** $f(n)=O(g(n))$ means $c \cdot g(n)$ is an **upper bound** on $f(n)$. There exists some constant $c$, such that $f(n) \leq c \cdot g(n)$ for every large enough $n$ (that is, for all $n \ge n_0$, for some constant $n_0$).
**(b)** $f(n)=\Omega(g(n))$ means $c \cdot g(n)$ is a **lower bound** on $f(n)$. Thus, there exists some constant $c$ such that $f(n) \ge c \cdot g(n)$ for all $n \ge n_0$.
**(c)** $f(n)=\Theta(g(n))$ means $c_1 \cdot g(n)$ is an **upper bound** on $f(n)$ and $c_2 \cdot g(n)$ is a **lower bound** on $f(n), for all $n \ge n_0$. Thus, there exist constants $c_1$ and $c_{2}$ such that $f(n) \leq c_{1} \cdot g(n)$ and $f(n) \geq c_{2} \cdot g(n)$ for all $n \geq n_{0}$. This means that $g(n)$ provides a nice, tight bound on $f(n)$.

We are not concerned with small values of $n$ (anything to the left of $n_0$ in the graphs).

### Examples
$$
\begin{aligned}
&f(n)=3 n^{2}-100 n+6=O\left(n^{2}\right), \text { because for } c=3,3 n^{2}>f(n)\\
&f(n)=3 n^{2}-100 n+6=O\left(n^{3}\right) \text { , because for } c=1, n^{3}>f(n) \text { when } n>3\\
&f(n)=3 n^{2}-100 n+6 \neq O(n) \text { , because for any } c>0, \text { cn }<f(n) \text { when } n>(c+100) / 3\\
&\begin{aligned}
&\text { since } n>(c+100) / 3 \Rightarrow 3 n>c+100 \Rightarrow 3 n^{2}>c n+100 n>c n+100 n-6 \\
&\Rightarrow 3 n^{2}-100 n+6=f(n)>c n
\end{aligned}
\end{aligned}
$$

$$
\begin{aligned}
&f(n)=3 n^{2}-100 n+6=\Omega\left(n^{2}\right), \text { because for } c=2,2 n^{2}<f(n) \text { when } n>100\\
&f(n)=3 n^{2}-100 n+6 \neq \Omega\left(n^{3}\right), \text { because for any } c>0, f(n)<c \cdot n^{3} \text { when } n>3 / c+3\\
&f(n)=3 n^{2}-100 n+6=\Omega(n), \text { because for any } c>0, f(n)<3 n^{2}+6 n^{2}=9 n^{2}\\
&\text { which is }<c n^{3} \text { when } n>\max (9 / c, 1) \text { ; }
\end{aligned}
$$

$f(n)=3 n^{2}-100 n+6=\Theta\left(n^{2}\right)$, because both $O$ and $\Omega$ apply;
$f(n)=3 n^{2}-100 n+6 \neq \Theta\left(n^{3}\right)$, because only $O$ applies;
$f(n)=3 n^{2}-100 n+6 \neq \Theta(n)$, because only $\Omega$ applies.


