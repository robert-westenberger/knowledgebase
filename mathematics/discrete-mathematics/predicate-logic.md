---
title: Predicate Logic
description: 
published: true
date: 2021-02-28T01:58:49.827Z
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

The following asserts that a predicate $P(n)$ is true for all values of $x$ in some set $D$, one would write

$$
\forall x \in D . \medspace P(n)
$$

To say that a predicate $P(x)$ is true for at least one value of $x$ in $D$ one writes: 
$$
\exists x \in D . P(x)
$$

Quantified predicates are themselves propositions and can be combined with logical connectives just like any other proposition.
$\neg \forall x P(x)$ is equivalent to $\exists x \neg P(x)$

$\neg \exists x P(x)$ is equivalent to $\forall x \neg P(x)$

(Essentially, we can pass the negation symbol over a quantifier, but that causes the quantifier to switch type).
