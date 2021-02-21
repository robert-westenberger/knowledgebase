---
title: Chapter 1: What is a Proof?
description: 
published: true
date: 2021-02-21T04:26:36.969Z
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

**Scratchwork:** We can factor $-x^3 + 4x$ to get $-x^3 + 4x = x(2-x)(2+x)$ .For $x$ between 0 and 2, all the terms on the right side are nonnegative. We can organize our observations into a formal proof.

**Proof:** Assume $0 \leq x \leq 2$. Then, $x$, $2-x$, and $2+x$ are all nonnegative. Therefore, the product of these terms is also nonnegative. Adding 1 to this product gives a positive number, so:
$$x(2-x)(2+x)+1>0$$
Multiplying out on the left side proves that 
$$
-x^{3}+4 x+1>0
$$ 
as claimed. $\blacksquare$

Note: Proofs typically begin with the word "Proof" and end with some sort of delimiter like $\square$, $\blacksquare$, or "QED".

### Method #2 - Prove the Contrapositive
An implication $P \text { IMPLIES } Q$ is logically equivalent to its contrapositive $\operatorname{NOT}(Q)$ IMPLIES $\operatorname{NOT}(P)$.

1) Write, "We prove the contrapositive:" and then tstate the contrapositive.
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

