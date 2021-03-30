---
title: Predicate Logic
description: 
published: true
date: 2021-03-30T17:20:28.220Z
tags: mathematics, discrete-mathematics
editor: markdown
---

## Predicates
A proposition whose truth depeonds on the value of one or more variables (called a **free variable**). "n is a perfect square" is a predicate, since you don't know its true or false until a value for n is provided.

Like other propositions, a predicate is often named with a letter. Furthermore, a function-like notation is used to denote a predicate supplied with specific variable vlaues. For example... 
$$
P(n)=" n \text { is a perfect square" }
$$
$P(4)$ would be true and $P(5)$ is false.
## Predicates and Quantifiers
We can assert that a predicate is **sometimes true**(existential qualification) or **always true** (universal quantificiation).
$$
\begin{array}{cc}
\text { Symbol } & \text { Meaning } \\
\hline 
\exists & \text { exists, there exists, there is } \\
\forall & \text { for all, every } \\
\end{array}
$$

The following asserts that there is a number less than 0.
$$
\exists x(x<0)
$$

The following asserts that every number is greater than or equal to 0.

$$
\forall x(x \geq 0)
$$

The following asserts that a predicate $P(n)$ is true for all values of $x$ in some set $D$

$$
\forall x \in D . \medspace P(n)
$$
The whole thing is read as, "for all $x$ in $D$, $P(x)$ is true".

To say that a predicate $P(x)$ is true for at least one value of $x$ in $D$ one writes: 
$$
\exists x \in D . \medspace P(x)
$$

This expression would be read as, "There exists an $x$ in $D$ such that $P(x)$ is true.

![quantifier_table.png](/quantifier_table.png)

### Binding Variables
When a quantifier is used on the variable $x$, we say this occurence of the variable is **bound**. An occurence of a variable that is not obund by a quantifier or set equal to a particular value is said to be **free**.

In the statement $\exists x(x+y=1)$, $x$ is bound and $y$ is free.
### Mixing Quantifiers

Many mathematical statements involve several quantifiers. Goldbach's Conjecture states:
$$
\text { "Every even integer greater than } 2 \text { is the sum of two primes." }
$$

Rewritten to make the use of quantification clearer: 
$$
\text { For every even integer } n \text { greater than } 2, \text { there exist primes } p \text { and } q \text { such that } \\  n=p+q
$$

Let Ev be the set of even integers greater than 2, and let Primes be the set of primes. Then we can write Goldbach’s Conjecture in logic notation as follows:


$$
\underbrace{\forall n \in \text { Ev }}_{\begin{array}{c}
\text { for every even } \\
\text { integer } n \geq 2
\end{array}} 
\underbrace{\exists p \in \text { Primes } \exists q \in \text { Primes. }}_{\begin{array}{c}
\text { there exist primes } \\
p \text { and } q \text { such that }
\end{array}} 
n=p+q
$$

### Reordering Quantifiers
Swapping quantifiers in Goldbach's Conjecture creates a false statement that every even number $\ge 2$ is the sum of the same two primes:
$$

\underbrace{\exists p \in \text { Primes } \exists q \in \text { Primes. }}_{\begin{array}{c}
\text { there exist primes } \\
p \text { and } q \text { such that }
\end{array}} 
\underbrace{\forall n \in \text { Ev }}_{\begin{array}{c}
\text { for every even } \\
\text { integer } n \geq 2
\end{array}} 
n=p+q
$$
### Variables Over One Domain
When all the variables in a formula are understood to take values from the same nonempty set $D$ it's conventional to omit mention of $D$.
For example instead of $\forall x \in D \exists y \in D . Q(x, y)$ we would write $\forall x \exists y . Q(x, y)$. The unnamed empty set that x and y range over is called the domain.

Goldbach's Conjecture could be expressed with all variables ranging over the domain $\natnums$ as 
$$
\forall n . \medspace n \in \mathrm{Ev} \longrightarrow(\exists p \exists q .  \medspace p \in \text { Primes } \wedge q \in \text { primes } \wedge n=p+q)
$$

### Negating Quantifiers
Quantified predicates are themselves propositions and can be combined with logical connectives just like any other proposition.


$\neg \forall x P(x)$ is equivalent to $\exists x \neg P(x)$

$\neg \exists x P(x)$ is equivalent to $\forall x \neg P(x)$

(Essentially, we can pass the negation symbol over a quantifier, but that causes the quantifier to switch type).

These two sentences mean the same thing:
$$\text{There does not exist anyone who likes skiing over magma.} \\ \text{ Everyone dislikes skiing over magma.}$$

We can express the equivalence in logic notation in this way:
$$
(\neg \exists x . Q(x)) \longleftrightarrow \forall x . \neg Q(x)
$$


### Validity for Predicate Formulas
For a predicate formula to be valid, a formula must evaluate to true no matter what the domain of discourse may be, no matter what values its variables may take over the domain, and no matter what interpreta- tions its predicate variables may be given. 

#### Example and Proof
A useful example of a valid assertion:
$$
\exists x \forall y . P(x, y) \longrightarrow \forall y \exists x . P(x, y)
$$
Lefthand side reads: There is an $x$ for which $P(x,y)$ is true for every $y$ 
Righthand side reads For every $y$, there is a $x$ for which $P(x,y)$ is true.

There is an $x$ for which $P(x,y)$ is true for every $y$ IMPLIES For every $y$, there is a $x$ for which $P(x,y)$ is true.

**Proof:** Let $D$ be the domain for the variables and $P_0$ be some binary predicate on $D$. We need to show that if $\exists x \forall y . P(x, y)$ holds under this interpretation, then so does $\forall y \exists x . P(x, y)$.

Suppose $\exists x \forall y . P(x, y)$. Some element $x_{0} \in D$ has the property that $P_{0}\left(x_{0}, y\right)$ is true for all $y \in D$. So for every $y \in D$, there is some $x \in D$, namely $x_0$, such that $P_{0}(x, y)$ is true. That is, $\forall y \exists x . P(x, y)$ holds under this interpretation. $\blacksquare$



