---
title: Algorithm Analysis
description: 
published: true
date: 2021-07-19T18:56:06.149Z
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

# Big O Notation
The Big O simplifies analysis of algorithms by ignoring levels of detail that don't impact comparison between algorithms. For example, difference between multiplicative constants. $f(n)=2 n$ and $g(n)=n$ are identical in Big O analysis

It is used extensively to estimate the number of operations an algorithm uses as its input grows. 


## Notation for Growth of Functions
Let $f$ and $g$ be functions from the set of integers or the set of real numbers to the set of real numbers. We say that $f(x)$ is $O(g(x))$ if there are constants $C$ and $k$ such that
$$
|f(x)| \leq C|g(x)|
$$
whenever $x>k$. (This is read as " $f(x)$ is big-oh of $g(x) . ")$
The constants $C$ and $k$ are called **witnesses** to the relationship of $f(x)$ is $O(g(x))$. To establish $f(x)$ is $O(g(x))$, we need find only one pair of constants $C$ and $k$, the witnesses, such that $|f(x)| \leq C|g(x)|$ whenever $x \gt k$.

Intuitively, the definition that $f(x)$ is $O(g(x))$ says that $f(x)$ grows slower than some fixed multiple of $g(x)$ as $x$ grows without bound.
![asymptotic-notation-graphs.png](/asymptotic-notation-graphs.png)
**(a)** $f(n)=O(g(n))$ means $c \cdot g(n)$ is an **upper bound** on $f(n)$. There exists some constant $c$, such that $f(n) \leq c \cdot g(n)$ for every large enough $n$ (that is, for all $n \ge n_0$, for some constant $n_0$).
**(b)** $f(n)=\Omega(g(n))$ means $c \cdot g(n)$ is a **lower bound** on $f(n)$. Thus, there exists some constant $c$ such that $f(n) \ge c \cdot g(n)$ for all $n \ge n_0$.
**(c)** $f(n)=\Theta(g(n))$ means $c_1 \cdot g(n)$ is an **upper bound** on $f(n)$ and $c_2 \cdot g(n)$ is a **lower bound** on $f(n), for all $n \ge n_0$. Thus, there exist constants $c_1$ and $c_{2}$ such that $f(n) \leq c_{1} \cdot g(n)$ and $f(n) \geq c_{2} \cdot g(n)$ for all $n \geq n_{0}$. This means that $g(n)$ provides a nice, tight bound on $f(n)$.

We are not concerned with small values of $n$ (anything to the left of $n_0$ in the graphs).


## General Procedure for finding Big $\Omega$ for a polynomial function
Let $m$ be a nonnegative integer, let $P(n)$ be a polynomial of degree $m$, and suppose the coefficient $a_{m}$ of $n^{m}$ is positive. To find big-Omega for $P(n)$ : Let $A=\frac{1}{2} a_{m}$, and let $a$ be the number obtained as follows:
1. Find the sum of the absolute values of all the coefficients of $P(n)$ except for $a_{m}$.
2. Multiply the result of step 1 by $\frac{2}{a_{m}}$.
3. Let $a$ be the larger of the number 1 and the result of step 2 .
Show that $A n^{m} \leq P(n)$ for every integer $n \geq a$.

### Example: Show $n^{4}-5 n-8$ is $\Omega\left(n^{4}\right)$
Observe the coefficient of the highest power is $1$ and the sum of the absolute values of its other coefficients is $|-5|+|-8| = 13$. Thus, we would take 
$$
A=\frac{1}{2} \quad \text { and } \quad a=\frac{2}{1}(|-5|+|-8|)
$$

and note that 

$$
a=\frac{2}{1}(|-5|+|-8|)=26, \quad \text { which is greater than }
$$

Requiring $n \ge a$ means that 
$$
n \geq \frac{2}{1}(|-5|+|-8|)
$$
and multiplying both sides by $\frac{1}{2} n^{3}$ gives

$$
\begin{aligned}
\frac{1}{2} n^{4} & \geq(|-5|+|-8|) n^{3} \\
&=5 n^{3}+8 n^{3} \\
& \geq 5 n+8 \quad \text { because } n \geq 1 \text { and so } 5 n^{3} \geq 5 n \text { and } 8 n^{3} \geq 8 .
\end{aligned}
$$

Hence, by transitivity of order and equality, 

$$
\frac{1}{2} n^{4} \geq 5 n+8 \quad \text { for every integer } n \geq a
$$

Subtracting the right-hand side from the left-hand side and adding $\frac{1}{2} n^{4}$ to both sides gives  

$$
n^{4}-5 n-8 \geq \frac{1}{2} n^{4} \quad \text { for every integer } n \geq a \text { . }
$$

Thus since $A=\frac12$, 
$$
n^{4}-5 n-8 \geq A n^{4} \quad \text { for every integer } n \geq a
$$

and so by definition of $\Omega$-notation, $n^{4}-5 n-8$ is $\Omega\left(n^{4}\right)$.
## Relation among $\mathbf{O}$-, $\mathbf{\Omega}-$, and $\Theta$- Notations
If $f$ and $g$ are real-valued functions defined on the same set of nonnegative integers, and if $f(n) \geq 0$ and $g(n) \geq 0$ for every integer $n \geq r$, where $r$ is a positive real number,
then $f(n)$ is $\Theta(g(n))$ if, and only if, $f(n)$ is $\Omega(g(n))$ and $f(n)$ is $O(g(n))$.
## Examples
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

# Growth Rates and Dominance Relations
$$
\begin{array}{|l||l|l|l|l|l|l|}
\hline n & \lg n & n & n \lg n & n^{2} & 2^{n} & n ! \\
\hline 10 & 0.003 \mu \mathrm{s} & 0.01 \mu \mathrm{s} & 0.033 \mu \mathrm{s} & 0.1 \mu \mathrm{s} & 1 \mu \mathrm{s} & 3.63 \mathrm{~ms} \\
20 & 0.004 \mu \mathrm{s} & 0.02 \mu \mathrm{s} & 0.086 \mu \mathrm{s} & 0.4 \mu \mathrm{s} & 1 \mathrm{~ms} & 77.1 \text { years } \\
30 & 0.005 \mu \mathrm{s} & 0.03 \mu \mathrm{s} & 0.147 \mu \mathrm{s} & 0.9 \mu \mathrm{s} & 1 \mathrm{sec} & 8.4 \times 10^{15} \mathrm{yrs} \\
40 & 0.005 \mu \mathrm{s} & 0.04 \mu \mathrm{s} & 0.213 \mu \mathrm{s} & 1.6 \mu \mathrm{s} & 18.3 \mathrm{~min} & \\
50 & 0.006 \mu \mathrm{s} & 0.05 \mu \mathrm{s} & 0.282 \mu \mathrm{s} & 2.5 \mu \mathrm{s} & 13 \text { days } & \\
\hline 100 & 0.007 \mu \mathrm{s} & 0.1 \mu \mathrm{s} & 0.644 \mu \mathrm{s} & 10 \mu \mathrm{s} & 4 \times 10^{13} \mathrm{yrs} & \\
1,000 & 0.010 \mu \mathrm{s} & 1.00 \mu \mathrm{s} & 9.966 \mu \mathrm{s} & 1 \mathrm{~ms} & & \\
10,000 & 0.013 \mu \mathrm{s} & 10 \mu \mathrm{s} & 130 \mu \mathrm{s} & 100 \mathrm{~ms} & & \\
100,000 & 0.017 \mu \mathrm{s} & 0.10 \mathrm{~ms} & 1.67 \mathrm{~ms} & 10 \mathrm{sec} & & \\
1,000,000 & 0.020 \mu \mathrm{s} & 1 \mathrm{~ms} & 19.93 \mathrm{~ms} & 16.7 \mathrm{~min} & & \\
10,000,000 & 0.023 \mu \mathrm{s} & 0.01 \mathrm{sec} & 0.23 \mathrm{sec} & 1.16 \text { days } & & \\
100,000,000 & 0.027 \mu \mathrm{s} & 0.10 \mathrm{sec} & 2.66 \mathrm{sec} & 115.7 \text { days } & & \\
1,000,000,000 & 0.030 \mu \mathrm{s} & 1 \mathrm{sec} & 29.90 \mathrm{sec} & 31.7 \text { years } & & \\
\hline
\end{array}
$$

Above: Running times of common funcitons measured in nanoseconds. The function $\lg n$ denotes the base-2 logarithm of $n$.

## Dominance Relations
Multiplicative constants are discarded with Big Oh Notation. $f(n)=0.001 n^{2}$ and $g(n)=1000 n^{2}$ are treated identically in big oh. 

Big Oh groups functions into a set of classes, such that all functions within a particular class are essentially equivalent. Functions $f(n)=$ $0.34 n$ and $g(n)=234,234 n$ belong in the same class, namely those that are order $\Theta(n)$. Furthermore, when two functions $f$ and $g$ belong to different classes, they are different with respect to our notation, meaning either $f(n)=O(g(n))$ or $g(n)=O(f(n))$, but not both.

A faster growing function **dominates** a slower growing one. When $f$ and $g$ belong to different classes (i.e. $f(n) \neq \Theta(g(n)))$, we say $g$ dominates $f$ when $f(n)=O(g(n))$. This is sometimes written $g \gg f$.

## Orders of Dominance

* **Constant functions**, $f(n)=1:$ Such functions might measure the cost of adding two numbers, printing out "The Star Spangled Banner," or the growth realized by functions such as $f(n)=\min (n, 100)$. In the big picture, there is no dependence on the parameter $n .$

* **Logarithmic functions**, $f(n)=\log n$ : Logarithmic time complexity shows up in algorithms such as binary search. Such functions grow quite slowly as $n$ gets big, but faster than the constant function (which is standing still, after all). 

* **Linear functions**, $f(n)=n:$ Such functions measure the cost of looking at each item once (or twice, or ten times) in an $n$ -element array, say to identify the biggest item, the smallest item, or compute the average value.

* **Superlinear functions**, $f(n)=n \lg n:$ This important class of functions arises in such algorithms as quicksort and mergesort. They grow just a little faster than linear, but enough so to rise to a higher dominance class.

* **Quadratic functions**, $f(n)=n^{2}:$ Such functions measure the cost of looking at most or all pairs of items in an $n$ -element universe. These arise in algorithms such as insertion sort and selection sort.

* **Cubic functions**, $f(n)=n^{3}:$ Such functions enumerate all triples of items in an $n$ -element universe. These also arise in certain dynamic programming algorithms.

* **Exponential functions**, $f(n)=c^{n}$ for a given constant $c>1:$ Functions like $2^{n}$ arise when enumerating all subsets of $n$ items. As we have seen, exponential algorithms become useless fast, but not as fast as...

* **Factorial functions**, $f(n)=n !:$ Functions like $n !$ arise when generating all permutations or orderings of $n$ items.

$$
n ! \gg 2^{n} \gg n^{3} \gg n^{2} \gg n \log n \gg n \gg \log n \gg 1
$$

# Working with Big Oh
## Adding Functions
The sum of two functions is governed by the dominanat one. Namely :
$$
f(n)+g(n) \rightarrow \Theta(\max (f(n), g(n)))
$$

## Multiplying Functions
Multiplying a function by a constant cannot affect its asymptotic behavior, because we can multiply the bounding constants in the Big Oh analysis to account for it: 


$$
\begin{aligned}
O(c \cdot f(n)) & \rightarrow O(f(n)) \\
\Omega(c \cdot f(n)) & \rightarrow \Omega(f(n)) \\
\Theta(c \cdot f(n)) & \rightarrow \Theta(f(n))
\end{aligned}
$$

Note that $c$ must be strictly positive. 

When two functions in a product are increasing, both are important. An $O(n ! \log n)$ function dominates $n !$ by just as much as $\log n$ dominates 1. In general: 
$$
\begin{aligned}
O(f(n)) \cdot O(g(n)) & \rightarrow O(f(n) \cdot g(n)) \\
\Omega(f(n)) \cdot \Omega(g(n)) & \rightarrow \Omega(f(n) \cdot g(n)) \\
\Theta(f(n)) \cdot \Theta(g(n)) & \rightarrow \Theta(f(n) \cdot g(n))
\end{aligned}
$$

# Reasoning About Efficiency
## Example: Selection Sort
<pre>
void selection_sort(item_type s[], int n) {
	int i, j; /* counters */
	int min; /* index of minimum */
  
  	for (i = 0; i < n; i++) { /* Goes around n times */
		min = i;
  		for (j = i + 1; j < n; j++) {
			if (s[j] < s[min]) {
				min = j;
			}
		}
		swap(&s[i], &s[min]);
	}
}

</pre>