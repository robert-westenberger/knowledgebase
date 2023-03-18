---
title: Algorithm Analysis
description: 
published: true
date: 2023-03-18T19:52:15.460Z
tags: data-structures, algorithms
editor: markdown
---

# The RAM Model of Computation
Machine-independent algorithm design depends upon a hypothetical computer called the Random Access Machine (RAM). This hypothetical computer has the following attributes:
* Each simple operation (+, *, -, =, if, call) takes exactly one time step.
* Loops and subroutines are a composition of many single-step operations. The time it takes to run through a loop or execute a subprogram depends on the number of loop iterations or the specific nature of the subprogram.
* Each memory access takes one time step. The RAM has unlimited memory.

Run time on the RAM is measured by counting the number of steps an algorithm takes on a given problem instance.

# Calculation Rules
Usually, the variable $n$ denotes input size. If the input is an array of numbers, $n$ will be the array length. 

$$
\text { If there are } k \text { nested loops, the time complexity is } O\left(n^k\right)
$$



## Loops 
A simple, single pass for loop, has a time complexity of $n$. A singly nested for loop will have a time complexity of $n^2$.

### Order of magnitude
A time complexity doesn't tell us the exact number of times the code inside a loop is executed, but it only shows us the order of magnitude.  

## Phases
If the algorithm consists of multiple consecutie phases, the total time complexity is the largest time coplexity of a single phase. The reason for this is that the slowest phase is usually the bottleneck of the code. 

For example, if the body of a function consists of a for loop, a nested for loop, and a for loop, then it's time complexity is $O\left(n^2\right)$.

## Several variables
Sometimes the time complexitty depends on several factors. In this case, the time complexity formula contains several variables.

For example, the time complexity of the following code is $O(\mathrm{~nm})$ :
```
for (int i = 1; i <= n; i++) {
   for (int j = 1; j <= m; j++) {
      // code
   }
}
```

## Recursion
The time complexity of a recursive function depends on the number of times the function is called and the time complexity of a single call. The total time complexity is the product of these values.

```
void f(int n) {
   if (n == 1) return;
   f(n-1);
}
```
The call $f(n)$ causes $n$ function calls, each of which have a constant ($O(1)$) time complexity. Thus, the total time complexity is $O(n)$.

```
void g(int n) {
	if (n == 1) return; 
  g(n-1);
  g(n-1);
}
```

In this case, each function call generates two other calls, except for (n = 1). The following table shows the function calls produced by this single call: 

$$
\begin{array}{rr}
\text { function call } & \text { number of calls } \\
\hline g(n) & 1 \\
g(n-1) & 2 \\
g(n-2) & 4 \\
\ldots & \ldots \\
g(1) & 2^{n-1}
\end{array}
$$

$$
1+2+4+\cdots+2^{n-1}=2^n-1=O\left(2^n\right)
$$



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
**(c)** $f(n)=\Theta(g(n))$ means $c_1 \cdot g(n)$ is an **upper bound** on $f(n)$ and $c_2 \cdot g(n)$ is a **lower bound** on $f(n)$, for all $n \ge n_0$. Thus, there exist constants $c_1$ and $c_{2}$ such that $f(n) \leq c_{1} \cdot g(n)$ and $f(n) \geq c_{2} \cdot g(n)$ for all $n \geq n_{0}$. This means that $g(n)$ provides a nice, tight bound on $f(n)$.

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

### Polynomial algorithms
An algorithm is polynomial if its time complexity is at most $O\left(n^k\right)$ where $k$ is a constant. All the above time complexities except $O\left(2^n\right)$ and $O(n !)$ are polynomial. In practice, the constant $k$ is usually small, and therefore a polynomial time complexity roughly means that the algorithm is efficient.

### More Esoteric Orders of Dominance
- Inverse Ackermann's function $f(n)=\alpha(n)$: Arises in the analysis of Union-Find data structure. It is the slowest growing complexity function. $\alpha(n)$ eventually gets to infinity as $n\rarr\infin$. The value of $\alpha(n)$ is smaller than $5$ for any value of $n$ that can be written in this physical universe.

- $f(n)=\text{log}\text{log}n$: The "log log" function. One example is the binary search on a sorted array of only $lg n$ items.

- $f(n)=\text{log}n/\text{log}\text{log}n$: Grows a little faster than $\text{log}n$, because its divided by an even slower growing function. Consider an $n$-leaf rooted tree of degree $d$. For binary trees, that is, when $d=2$, the height $h$ is given
$$
n =2^h\rarr h=\text{lg}n
$$
by taking the log of both sides of the equation. Now consider the height of such a tree when the degree $d=\text{log}n$. Then

$$
n = (\text{log}n)^h \rarr h = \text{log}n/\text{log}\text{log}n
$$

- $f(n)=\text{log}^2n$:
- $f(n)=\sqrt{n}$:
- $f(n)=n^{(1+\epsilon)}$:
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
  		for (j = i + 1; j < n; j++) { /* Goes around n - (i+1) times, where i is the index of the outer loop*/
			if (s[j] < s[min]) {
				min = j;
			}
		}
		swap(&s[i], &s[min]);
	}
}

</pre>

In the above algorithm, the number of times the if statement is executed is given by 

$$T(n)=\sum_{i=0}^{n-1} \sum_{j=i+1}^{n-1} 1=\sum_{i=0}^{n-1} n-i-1$$


What this sum is doing is adding up the non-negative integers in decreasing order starting from $n-1$, which is

$$
T(n)=(n-1)+(n-2)+(n-3)+\ldots+2+1
$$

This yields $T(n) \approx(n-1) n / 2=O\left(n^{2}\right)$

# Classes of Summation Formulae
## Sum of a Power of Integers
In general, 

$$
S(n, p)=\sum_{i=1}^{n} i^{p}=\Theta\left(n^{p+1}\right)
$$

for $p \ge 0$. Thus, the sum of squares is cubic, and the sum of cubes if quartic, and so on. 

For $p \lt -1$, this sum $S(n,p)$ always converges to a constant as $n \rightarrow \infty$, while for $p \ge 0$ it diverges. The interesting case between these is the Harmonic numbers, $H(n)=\sum_{i=1}^{n} 1 / i=\Theta(\log n)$.

## Sum of a Geometric Progression
In geometric progerssions, the index of the loop affecst the exponent, that is, 
$$
G(n, a)=\sum_{i=0}^{n} a^{i}=\left(a^{n+1}-1\right) /(a-1)
$$

# Logarithms
See 
- [Properties of Logarithms](/mathematics/Logarithms/properties-of-logarithms)
- [Logarithm Identity Proofs](/mathematics/Logarithms/identity-proofs)
# Limits and Dominance Relations
We say that $f(n)$ **dominates** $g(n)$ if $\lim _{n \rightarrow \infty} g(n) / f(n)=0$.



## Example
Suppose $f(n)=2 n^{2}$ and $g(n)=n^{2}$. Clearly $f(n)>g(n)$ for all $n$, but it does not dominate since
$$
\lim _{n \rightarrow \infty} \frac{g(n)}{f(n)}=\lim _{n \rightarrow \infty} \frac{n^{2}}{2 n^{2}}=\lim _{n \rightarrow \infty} \frac{1}{2} \neq 0
$$
This is to be expected because both functions are in the class $\Theta\left(n^{2}\right) .$ What about $f(n)=n^{3}$ and $g(n)=n^{2} ?$ Since
$$
\lim _{n \rightarrow \infty} \frac{g(n)}{f(n)}=\lim _{n \rightarrow \infty} \frac{n^{2}}{n^{3}}=\lim _{n \rightarrow \infty} \frac{1}{n}=0
$$

the higher-degree polynomial dominates. This is true for any two polynomials, that is, $n^{a}$ dominates $n^{b}$ if $a>b$ since
$$
\lim _{n \rightarrow \infty} \frac{n^{b}}{n^{a}}=\lim _{n \rightarrow \infty} n^{b-a} \rightarrow 0
$$
Thus, $n^{1.2}$ dominates $n^{1.1999999}$. Now consider two exponential functions, say $f(n)=3^{n}$ and $g(n)=2^{n}$. Since
$$
\lim _{n \rightarrow \infty} \frac{g(n)}{f(n)}=\frac{2^{n}}{3^{n}}=\lim _{n \rightarrow \infty}\left(\frac{2}{3}\right)^{n}=0
$$

the exponential with the higher base dominates. 