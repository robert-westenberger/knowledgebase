---
title: Problems 1
description: 
published: true
date: 2021-03-11T21:30:52.117Z
tags: computer-science, mathematics, discrete-mathematics
editor: markdown
---

# Problems 1


### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 1
A real number r is called sensible if there exist positive integers $a$ and $b$ such
that $\sqrt{a/b} = r$. For example, setting $a = 2$ and $b = 1$ shows that $\sqrt 2$ is sensible. Prove that $\sqrt[3]2$ is not sensible. (Consider only positive real roots in this problem).

#### Solution
We use proof by contradiction. Suppose that $\sqrt[3]2 = \frac ab$ where a and b are two positive integers.

We cube both sides to get $2 = \frac{a^3}{b^3}$.

We divide both sides to get $2b^3 = a^3$. This implies a is an even integer. If $a^3$ is an even integer, that means that $a$ is an even integer as well.

We can rewrite $a$ as $a=2n$ for some unknown integer $n$. Therefore,
$$(2n)^3 = 2b^3$$
$$8n^3 = 2b^3$$
$$4n^3 = b^3$$

We see that b is also even (its a multiple of 4). Since a and b are both even, they are not coprime numbers, which is a contradiction.

Since we have a contradiction, we must assume that $\sqrt[3] 2$ is irrational. $\blacksquare$


### Problem 1 (From In-Class Problems MIT OCW 6.042J Spring '15)

The Pythagorean Theorem says that if a and b are the lengths of the sides of a right triangle, and c is the length of its hypotenuse, then
$$a^2 + b^2 = c^2$$
In this problem we'll examine a  particularly simple “proof without words” of the theorem.

Suppose you are given four different colored copies of a right triangle with sides of lengths a, b and c, along with a suitably sized square, shown below.![pythagorean_theorem_problem.png](/pythagorean_theorem_problem.png)

**(a)** You will first arrange the square and four triangles so they form a $c \medspace x \medspace c$ square. From this arrangement you will see that the square is $(b - a) \medspace x \medspace (b-a)$

**(b)** You will then arrange the same shapes so they form two squares, one $a \medspace x \medspace a$ and the other $b \medspace x \medspace b$.
You know that he area of an $s \medspace x \medspace s$ square is $s^2$. Appealing to the principle that **area is preserved by rearranging**, we can conclude that $a^2 + b^2 = c^2$ as claimed.
One concern is that there might be something special about the shape of these particular triangles and squares that makes the rearranging possible - for exmaple, suppose $a=b$. 
**(c)** How would you respond to this concern?
**(d)** Another concern is that a number of facts about right triangles, squares and lines are being implicitly assumed in justifying the rearrangements into squares. Enumerate some of these assumed facts.

#### Solution (WIP)
$$a=3 \quad b=4 \quad c=5$$

**a)** ![pythag_a.png](/pythag_a.png)
We see that that the square is $(b-a) \medspace x \medspace (b-a)$.

**b)**
![pytthag_b.png](/pytthag_b.png)
Triangles rearranged to form bxb square and a cxc square.
### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 2
Translate the following sentence into a predicate formula: 

*There is a student who has emailed exactly two other people in the class, besides possibly herself.*

The domain of discourse should be the set of students in the class; in addition, the only predicates that you may use are equality and E(x, y), meaning that “x has sent email to y.”
#### Solution

$$
\begin{aligned}
&\exists x \exists y \exists z . E(x, y) \wedge E(x, z) \wedge\\
&x \neq y \wedge x \neq z \wedge y \neq z \wedge\\
&\forall s, E(x, s) \longrightarrow s=x \vee s=y \vee s=z
\end{aligned} \\

\hspace 15.5em \blacksquare
$$

The above is translated to: "There exists students $x$, $y$, and $z$ where $x$ send an email to $y$ AND $x$ sent an email to $z$ AND $x$ is not the same as $y$ AND $x$ is not the same as $z$ and $y$ is not the same as $z$ AND for all students $s$, x sent an email to a student s where the student s is x OR the student s is y OR the student s is z.

### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 3
Express each of the following predicates and propositions in formal logic notation. The domain of discourse is the nonnegative integers, $\natnums$

In addition to the propositional operators, variables and quantifiers, you may define predicates using addition, multiplication, and equality symbols, but no constants (like 0, 1, . . .). For example, the proposition “n is an even number” could be written
$$
\exists m .(m+m=n)
$$

**(a)** n is the sum of three perfect squares.

Since the constant 0 is not allowed to appear explicitly, the predicate “$x = 0$” can’t be written directly, but note that it could be expressed in a simple way as:
$$x + x = x$$

Then the predicate $x>y$ could be expressed 
$$
\exists w. \medspace (y+w=x) \wedge(w \neq 0)
$$

Note that we’ve used “$w \ne 0$” in this formula, even though it’s technically not allowed. But since “$w \ne 0$” is equivalent to the allowed formula “$¬(w + w = w)$,” we can use “$w \ne 0$” with the understanding that it abbreviates the real thing. And now that we’ve shown how to express “$x > y$”, it’s ok to use it too.

**(b)** $x > 1$.
**(c)** $n$ is a prime number. 
**(d)** $n$ is a product of two distinct primes. 
**(e)** There is no largest prime number. 
**(f)** (Goldbach Conjecture) Every even natural number $n > 2$ can be expressed as the sum of two primes. 
**(g)** (Bertrand’s Postulate) If $n > 1$, then there is always at least one prime $p$ such that $n < p < 2n$.

#### Solution (My own answers probably wrong regarding valid quantifier syntax, loop back to this)
a) $\exists m=(m \cdot m=d)\wedge (d+d+d=n)$
b) A unique property of one is that multiplying one by itself is idempotent. Adding one to itself is not. Also, squaring one equals itself. Any number greater than one, when we square it, will be greater than the value we squared.
$$\exists x .(x \ne 0) \wedge (x^x - x \ne 0)$$
$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$ We define $x=1$ as $\forall y . \medspace x y=y$ and then express $x \gt 1$ as $\exists y . \medspace (y=1) \wedge(x>y)$

c) If a number $n$ is prime, it is greater than 0 and there are no numbers $y$ and $z$ that add to it.
$$\exists n.(n \ne 0) \wedge \neg(y + z =n)$$

$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$ IS-PRIME $(n)::=(n>1) \wedge \neg(\exists x \exists y .(x>1) \wedge(y>1) \wedge(x \cdot y=n))$

d) n is a product of two numbers, which themselves are numbers for which there does not exist two numbers that add up to them. 

$$\text {Is-Product-of-Primes}(n)::= \exists x \exists y. \medspace \text{IS-PRIME}(x) \wedge  \text{IS-PRIME}(y) \wedge x \not = y \medspace \wedge x \cdot y = n  $$

e) There is no largest prime number.

$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$  $\neg(\exists p .$ IS-PRIME $(p) \wedge(\forall q .$ IS-PRIME $(q) \longrightarrow p \geq q))$
"There does not exist a prime number $p$ and for all numbers $q$, if $q$ is prime then p is greater than $q$."

f) (Goldbach Conjecture) Every even natural number $n>2$  can be expressed as the sum of two primes.

Define a proposition Is-Two(n) using the fact that two is the only number that Is-Prime and Is-Even (we can use this proposition since its in the question description)

$$\text {Is-Two}(n)::= \text {Is-Prime}(n) \wedge \text {Is-Even}(n) $$

Using the n > 1 and Is-Two estalished above...

$$\text {Is-Greater-Than-Two}(n)::= (n > 1) \medspace \wedge \medspace \neg (\text {Is-Two}(n))$$

$$\text {Is-Sum-of-Primes}(n)::= \exists x \exists y. \medspace \text{IS-PRIME}(x) \wedge  \text{IS-PRIME}(y)  \wedge x + y = n $$

$$\forall n. \medspace \text {Is-Greater-Than-Two}(n) \wedge \text {Is-Sum-of-Primes}(n)$$

My answer is missing the actual implication part...

$$
\forall n \medspace \text {Is-Greater-Than-Two}(n) \longrightarrow  \text {Is-Sum-of-Primes}(n)
$$
$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$ We can define $n \gt 2$ with the formula $\exists y \cdot(y=1) \wedge(x>y+y)$. $n = 2k$ can be expressed as $n=k+k$. The conjecture can be expressed as:

$$
\forall n .((n>2 \wedge \exists k . n=2 k) \longrightarrow \exists p \exists q . \text { IS-PRIME }(p) \wedge \text { IS-PRIME }(q) \wedge(n=p+q)))
$$


g) (Bertrand’s Postulate) If $n > 1$, then there is always at least one prime $p$ such that $n < p < 2n$.

$$\forall n. \medspace n \gt 1 \longrightarrow \exists p. \text { IS-PRIME }(p) \wedge \medspace n \lt p \lt 2n$$

$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$$\forall n .((n>1) \longrightarrow(\exists p .$ IS-PRIME $(p) \wedge(n<p) \wedge(p<2 n)))$

### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 4
If a set, $A$, is finite, then $|A|<2^{|A|}=|\mathcal{P}(A)|$, and so there is no surjection from set $A$ to its powerset. Show that this is still true if $A$ is infinite. Hint: Remember Russel's paradox and consider $\{x \in A \mid x \notin f(x)\}$ where $f$ is such a surjection.

#### Solution
**Scratch:** Proving by contradiction. 

Suppose there was a surjective function $f$ that maps a set $A$ to its powerset $P(A)$.

Let $W$ be the set of $x$ in $A$ that are not in the image of $f$. 

So by definition we get the following biconditional for all $x$ in $A$.. if $x$ is in $W$ that means that $x$ isn't in the image of $f$ and if $x$ isn't in the image of $f$ that means its in $W$.

We know that every element of $W$ is in $A$ by the definition of the subset of a set.

This means that $W$ is also a member of $P(A)$ by the definition of a powerset (the powerset contains all subsets of its set, $W$ is a subset of $A$ so obviously it will be in the powerset as well).

Since $f$ is a surjection from $A$ to $P(A)$, there exists some $a$ in $A$ whose image is $W$.

So by our earlier biconditional we can replace $W$ with $f(a)$ and get 
$$
(x \in f(a)) \longleftrightarrow(x \notin f(x))
$$
Substituting $a$ for $x$ yields a contradiction, proving there cannot be such an $f$.

**Proof:** 
Proof by contradiction. Suppose there was a surjection $f: A \rightarrow \mathcal{P}(A)$ for some set $A$. Let $W::=\{x \in A \mid x \notin f(x)\}$. So by definition
$$
(x \in W) \longleftrightarrow(x \notin f(x)) \hspace{6em} \text{(1)}
$$
for all $x \in A$. But $W \subseteq A$ by definition and hence is a member of $P(A$). This means that $W = f(a)$ for some $a \in A$, since $f$ is a surjection to $P(A)$. So we have from $(1)$ 
$$
(x \in f(a)) \longleftrightarrow(x \notin f(x))  \hspace{6em} \text{(2)}
$$
for all $x \in A$. Substituting $a$ for $x$ in $(2)$ yields a contradiction, proving there cannot be such an $f$.
$$\hspace{32em} \blacksquare$$

### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 5
**(a)** Prove that 
$$
\exists z. \medspace \lbrack P(z) \wedge Q(z)] \longrightarrow \lbrack \exists x . \medspace P(x) \wedge \exists y . \medspace Q(y)] \hspace{6em} \text{(1)}
$$
is valid. 
**(b)**  Prove that the converse of $(1)$ is not valid by describing a counter model as in Week 2 Notes.
#### Solution (From book)
Assume 
$$
\exists z . \medspace \lbrack P(z) \wedge Q(z)]
$$
That is, $P(z) \wedge Q(z)$ holds for some element $z$ of the domain. Let $c$ be this element, that is, we have $P(c) \wedge Q(c)$.

In particular, $P(c)$ holds by itself. So we conclude (By Existential Generalization) $\exists x \medspace P(x)$. We conclude $\exists y \medspace Q(y)$ similarly.
##### Scratch 
The proposition states that if there exists some $z$ for which $P(z)$ and $Q(z)$ are true then there exists some $x$ for which $P(x)$ is true and there exists some y for which $Q(y)$ is true.

Let $D$ be the domain for the variables and $P_0$, and $Q_0$ be some unary predicates on $D$.


We need to show that if $\exists z . \lbrack P(z) \wedge Q(z)]$ holds, then so does $\lbrack \exists x . \medspace P(x) \wedge \exists y . \medspace Q(y)]$.

So suppose $\exists z . \lbrack P(z) \wedge Q(z)]$. So some element $z_0 \in D$ has the property that $P_0 (z) \wedge Q_0 (z)$ is true. 


Suppose $\lbrack \exists x . \medspace P(x) \wedge \exists y . \medspace Q(y)]$. There exists some $x_0 \in D$ that has the property $P_0(x)$ is true and there exists some $y_0 \in D$ that $Q_0(y)$ is true.
