---
title: Mathematical Induction
description: 
published: true
date: 2021-04-12T19:14:52.332Z
tags: discrete-mathematics
editor: markdown
---

# Induction

Induction proofs have two parts.
1. Show that the statement holds for the positive integer $1$.
2. Show that the statement holds for the next larger integer.

Induction is based on the rule of inference that tells us that if $P(1)$ and $\forall k(P(k) \rightarrow P(k+1))$ are true for the domain of positive integers, then $\forall n P(n)$ is true.