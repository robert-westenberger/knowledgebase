---
title: Chapter 1: What is a Proof?
description: 
published: true
date: 2021-02-21T01:35:18.247Z
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

#### Modus Ponens
$$
\frac{P, \quad P \text { IMPLIES } Q}{Q}
$$
A proof of $P$ together with a proof $P \text{IMPLIES} Q$ is a proof of $Q$.