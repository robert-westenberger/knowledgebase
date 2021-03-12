---
title: Types Of Proofs
description: 
published: true
date: 2021-03-12T06:13:30.250Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Types of Proofs


## Proving an Implication
Propositions of the form "If $P$, then $Q$" are called implications. 

Its often rephrased as $P \text { IMPLIES } Q$

* Quadratic Formula - If $ax^2 + bx + c = 0 \medspace \text{and} \medspace a \not = \text{, then} \medspace x=\left(-b \pm \sqrt{b^{2}-4 a c}\right) / 2 a$.

### Method #1 
In order to prove $P \text { IMPLIES } Q$: 
1) Write, "Assume P".
2) Show that Q logically follows. 

#### Example of Method #1

**Theorem:** $\text { If } 0 \leq x \leq 2 \text { , then }-x^{3}+4 x+1>0$

**Scratchwork:** We can factor $-x^3 + 4x$ to get $-x^3 + 4x = x(2-x)(2+x)$ .For $x$ between 0 and 2, all the terms on the right side are nonnegative. We can organize our observations into a formal proof.

**Proof:** Assume $0 \leq x \leq 2$. Then, $x$, $2-x$, and $2+x$ are all nonnegative. Therefore, the product of these terms is also nonnegative. Adding 1 to this product gives a positive number, so:
$$x(2-x)(2+x)+1>0$$
Multiplying out on the left side proves that 
$$
-x^{3}+4 x+1>0
$$ 
as claimed. $\blacksquare$

Note: Proofs typically begin with the word "Proof" and end with some sort of delimiter like $\square$, $\blacksquare$, or "QED".
### Example 2 of Method #1
**Theorem:** For all integers $a$, $b$, and $c$, if $a/b$ and $b/c$, then $a/c$.
**Scratch:** We have to explain the meaning of $a/b$ and $b/c$, and why this gives us the conclusion $a/c$. Another way of saying $a/b$ is to say $b = ka$ for some integer $k$ (in other words, $b$ is a multiple of $a$. We are going for the fact that $c = la$ for some integer $l$ (because we want $c$ to be a multiple of $a$).
**Proof:** 

1. Let $a$, $b$, and $c$ be integers. Assume that $a/b$ and $b/c$.
(Our assumption)

2. In other words, $b$ is a multiple of $a$ and $c$ is a multiple of $b$.
(Division is the inverse of multiplication. $a/b$ is defined to be the unique solution to the equation $bx = a$)

3. So there are integers $k$ and $j$ such that $b=ka$ and $c=jb$.
(Follows from line 2)

4. Combining these(through substitution) we get that $c = jka$. 
(Just combining

5. But $jk$ is an integer, so this says that $c$ is a multiple of $a$. 

6. Therefore $a/c$. $\blacksquare$
### Method #2 - Prove the Contrapositive
An implication $P \text { IMPLIES } Q$ is logically equivalent to its contrapositive $\operatorname{NOT}(Q)$ IMPLIES $\operatorname{NOT}(P)$.

1) Write, "We prove the contrapositive:" and then state the contrapositive.
2) Proceed as in Method #1. 

#### Example of Method #2
**Theorem:** $\text{If r is irrational, then} \medspace \sqrt r \medspace \text{is also irrational}$.
**Scratchwork:** A number is irrational when there is no quotient of integers to which it is equal. We must show that if r is not a ratio of integers, then $\sqrt r$ is also not a ratio of integers. We can eliminate both not's and simplify the proof by using the contrapositive instead.
**Proof:** We prove the contrapositive: if $\sqrt r$ is rational, then $r$ is rational. Assume that $\sqrt r$ is rational. Then there exists integers $m$ and $n$ such that:
$$\sqrt r = \frac m n$$
Squaring both sides gives: 
$$r = \frac{m^2}{n^2}$$
Since $m^2$ and $n^2$ are integers, r is also rational. $\blacksquare$

## Proving an "If and Only If"
Many theorems assert that two statements are logically equivalent; that is one holds if and only if (iff) the other does. 

Example: Two triangles have the same side lengths if and only if two side lengths and the angle between those sides are the same.

### Method #1: Prove Each Statement Implies the Other
The statement $P \text { IFF } Q$ is equivalent to the two statements $P \text { IMPLIES } Q$ and $Q \text { IMPLIES } P$. You can prove "iff" by proving two implications.
1) Write, "We prove P imoplies Q and vice-versa"
2) Write, “First, we show P implies Q.” . 
3) Write, “Now, we show Q implies P.”

### Method #2: Construct a Chain of Iffs
1. Write, “We construct a chain of if-and-only-if implications.” 
2. Prove P is equivalent to a second statement which is equivalent to a third statement and so forth until you reach $Q$.


#### Example of Method #2
The standard deviation of a sequence of values $x_{1}, x_{2}, \ldots, x_{n}$ is defined to be:
$$
\sqrt{\frac{\left(x_{1}-\mu\right)^{2}+\left(x_{2}-\mu\right)^{2}+\cdots+\left(x_{n}-\mu\right)^{2}}{n}}
$$
where $\mu$ is the average/mean of the values.
$$
\mu::=\frac{x_{1}+x_{2}+\cdots+x_{n}}{n}
$$
**Theorem:** The standard deviation of a sequence of values $x_{1}, x_{2}, \ldots, x_{n}$ is zero iff all the values are equal to the mean.

For example, the standard deviation of class scores is 0 iff everyone scored exactly the class average.

**Proof:** We construct a chain of "iff" implications, starting with the statement that the standard deviation is zero.
$$
\sqrt{\frac{\left(x_{1}-\mu\right)^{2}+\left(x_{2}-\mu\right)^{2}+\cdots+\left(x_{n}-\mu\right)^{2}}{n}}=0
$$

Now since zero is the only number whose root is 0, the above equation holds iff 
$$
\left(x_{1}-\mu\right)^{2}+\left(x_{2}-\mu\right)^{2}+\cdots+\left(x_{n}-\mu\right)^{2}=0
$$
Squares of real numbers are always nonnegative, so every term on the left hand side is nonnegative. This means that the above equation holds iff 
*Every term on the left-hand side is zero.*
But a term $\left(x_{i}-\mu\right)^{2}$ is zero iff $x_{i}=\mu$, so the preceding statement is true iff every $x_i$ equals the mean. $\blacksquare$

## Proof by Cases
Otherwise known as proof by exhaustion. 

**Theorem:** If an integer is a perfect cube, then it must be either a multiple of 9, 1 more than a multiple of 9, or 1 less than a multiple of 9.

**Proof:** The proof is by case analysis. Each perfect cube is the cube of some integer n, where n is either a multiple of 3, 1 more than a multiple of 3, or 1 less than a multiple of 3. So these three cases are exhaustive:
*  Case 1: If $n=3p$, then $n^3 = 27p^3$, which is a multipole of 9.
* Case 2: If $n = 3p + 1$, then $n^3 = 27p^3 + 27p^2 + 9p + 1$, which is 1 more than a multiple of 9. For instance, if $n = 4$ then $n^3 = 64 = 9×7 + 1$.
* Case 3: If $n = 3p − 1$, then $n3 = 27p^3 − 27p^2 + 9p − 1$, which is 1 less than a multiple of 9. For instance, if $n = 5$ then $n3 = 125 = 9×14 − 1$. 
$\blacksquare$

## Proof by Contradiction
Otherwise known as an **indirect proof**, you show that if a proposition were false, then some false fact would be true. Since a false fact by definition can't be true, then the proposition must be true.

### Method
1. Write "We use proof by contradiction."
2. Write, "Suppose P is false."
3. Deduce something known to be false (a logical contradiction). 
4. Write, "This is a contradiction. Therefore, P must be true."


#### Example 
**Theorem:** $\sqrt 2$ is irrational.

**Proof:** We use proof by contradiciton. Suppose that the claim is false and 
$\sqrt 2$ is rational. We can write $\sqrt 2$ as a fraction $n/d$ in lowest terms.

Squaring both sides gives us $2 = n^2/d^2$ so 2d^2 = n^2. This implies that n is a multiple of 2. Therefore $n^2$ must be a multiple of 4. But since $2d^2 = n^2$, we know $2d^2$ is a multiple of 4 and so $d^2$ is a multiple of 2. That implies d is a multiple of 2.

So, the numerator and the denominator have 2 as a common factor, which contradicts that fact that $n/d$ is in lowest terms. Thus, $\sqrt 2$ must be irrational. $\blacksquare$

#### Example 2
**Theorem:** There are infinitely many primes.
**Proof:** 
We use proof by contradiction. Suppose the theorem is false, that there are actualy a finite number of primes. Then there must be a last, largest prime $p$. 

Consider the number 
$$
N=p !+1=(p \cdot(p-1) \cdots 3 \cdot 2 \cdot 1)+1
$$
$N$ is certainly larger than $p$ and not divisible by any number less than or equal to $p$, since every number less than or equal to $p$ divides $p!$. Thus, the prime factorization of $N$ contains prime numbers (possibly just $N$ itself) all greater than $p$. So $p$ is not the largest prime, a contradiction. Therefore there are infinitely many primes. $\blacksquare$


##### Example 2, line by line
1. Suppose there are only finitely many primes. (this is a premise. Note the use of “suppose.”)
2. There must be a largest prime, call it $p$. (follows from line 1, by the definition of “finitely many.”)
3. Let $N = p! + 1$ (The key insight of the proof.)
4. $N$ is larger than $p$ (be definition of $p!$
5. $N$ is not divisible by any number less than or equal to $p$ (by definiton, $p!$ is divisible by each number $\le$ p, so $p!+1$ is not.
6. The prime factorization of $N$ contains prime numbers greater than $p$. (since $N$ is divisible by each prime number in the prime factorization of $N$, and by line 5).
7. Therefore $p$ is not the largest prime (by line 6, $N$ is divisible by a prime larger than $p$).
8. This is a contradiction (from line 2 and 7; the largest prime is $p$ and there is a prime larger than $p$). 
9. Therefore there are infinitely many primes (from line 1 and lien 8: our only premise lead to a contradiction, so the premise is false).

