---
title: Mathematical Induction
description: 
published: true
date: 2021-04-13T17:54:12.742Z
tags: discrete-mathematics
editor: markdown
---

# Induction

Induction proofs have two parts.
1. Show that the statement holds for the positive integer $1$. (the **basis step**)
2. Show that the statement holds for the next larger integer. ($P(k) \rightarrow P(k+1)$ is true for all positive integers $k$, the **inductive step**).

Induction is based on the rule of inference that tells us that if $P(1)$ and $\forall k(P(k) \rightarrow P(k+1))$ are true for the domain of positive integers, then $\forall n P(n)$ is true.

Induction can be used only to prove results obtained some other way. It is not a tool for discovering formulae or theorems.

Expressed as a rule of inference, induction can be stated as
$$
(P(1) \wedge \forall k(P(k) \rightarrow P(k+1))) \rightarrow \forall n P(n)
$$

Mathmatical induction relies on the [Well Ordering Principle](/mathematics/discrete-mathematics/well-ordering-principle).

## Template for Proofs by Mathematical Induction
1. Express the statement that is to be proved in the form "for all $n \geq b, P(n)$", for a fixed integer $b$. For statements of the form "$P(n)$ for all positive integers $n$, let $b=0$. For some statements of the form $P(n)$, such as inequalities, you may need to determine the appropriate value of $b$ by checking the truth tables of $P(n)$ for small values of $n$. 

2. Write out the words "Basis Step". Then show $P(b)$ is true, taking care that the correct value of $b$ is used. 

3. Write out the words "Inductive Step", and state the inductive hypothesis in the form, "Assume $P(k)$ is true for an arbitrary fixed integer $k \ge b$."

4. State what needs to be proved under the assumption that the inductive hypothesis is true. That is, write out what $P(k+1)$ says.

5. Prove the statement $P(k+1)$ making use of the assumption $P(k)$. Be sure that your proof is valid for all integers $k$ with $k \ge b$, taking care that the proof works for small values of $k$, including $k=b$.

6. Clearly identify the conclusion of the inductive step, such as by saying, "This completes the inductive step."

7. After completing the basis and inductive step, state the conclusion, "By mathematical induction, $P(n)$ is true for all integers $n$ with $n \ge b$. 

## Examples 
