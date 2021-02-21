---
title: Chapter 1: What is a Proof?
description: 
published: true
date: 2021-02-21T02:06:07.092Z
tags: computer-science, mathematics, book-notes, discrete-mathematics
editor: markdown
---

# What is a Proof? 

## Propositions
A **mathematical proof** of a **proposition** is a chain of **logical deductions** leading to the proposition from a base set of **axioms**. 

A **proposition** is a statement that is either true or false. 

**Claim:** For every nonnegative integer n the value of $n^2+n+41$ is prime.
$$p(n) ::=n^2 + n + 41$$

We can check $n=0$ to $n=39$ and the claim holds true. However, for $n=40$ we get $40^2 + 40 + 41 = 41* 41$ which is not prime. This example highlights, in general, you can't check a claim about an infinite set by checking a finite sample of its elements, no matter how large the sample. 

There is a special notation for propositions about all numbers or all items of a certain kind: 

$$\forall n \in \natnums .p(n) \medspace \text{is prime.}$$

It reads: "For all n in the set of nonnegative integers, p(n) is prime.

## Predicates
A **predicate** can be understood as a proposition whose truth depeonds on the value of one or more variables. "n is a perfect square" is a predicate, since you don't know its true or false until a value for n is provided.

## The Axiomatic Method

**Axioms** are statements or propositions taken to be true. Using these axioms, proofs can be developed. A **proof** is a sequence of logical deductions from axioms and previously proved statements that conludes with the proposition in question. 

* Important true propositons are called theorems. 
* A lemma is a preliminary proposition useful for proving later propositions. 
* A crollary is a proposition that folows in just a few logical steps from a theorem.

## Our Axioms

### Logical Deductions
Logical deductions, or inference rules, are used to proce new propositions by using previously proved ones. 

$$
\frac{P, \quad P \text { IMPLIES } Q}{Q}
$$
A proof of $P$ together with a proof $P \medspace \text{IMPLIES} \medspace Q$ is a proof of $Q$.

When the statements are above the line, called the **antecedents**, are proved, we can consider the statement below the line, the **conclusion** or **consequent**, to be true.

$$
\frac{P \text { IMPLIES } Q, \quad Q \text { IMPLIES } R}{P \text { IMPLIES } R}
$$
$$
\frac{\text { NOT }(P) \text { IMPLIES } \operatorname{NOT}(Q)}{Q \text { IMPLIES } P}
$$

Each step in a proof should be clear and "logical"; in particular, one should state what previously proved facts are used to derive each new conclusion.

### Patterns of Proof

A proof can be any sequence of logical deductions. Many proofs follow one of a handful of standard templates. Each proof has it own details, of course, but these templates at least provide you with an outline to fill in.

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




