---
title: Mathematical Induction
description: 
published: true
date: 2021-04-13T15:57:00.719Z
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