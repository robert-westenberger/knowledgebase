---
title: Induction Exercises
description: 
published: true
date: 2021-04-13T19:12:11.603Z
tags: discrete-mathematics
editor: markdown
---

# Rosen Discrete Mathematics 7th Edition Section 


### 1
There are infinitely many stations on a train route. Suppose
that the train stops at the first station and suppose
that if the train stops at a station, then it stops at the next
station. Show that the train stops at all stations.
#### Solution
Let $P(n)$ be the statement that the train stops at station $n$. We want to prove that $P(n)$ is true for all positive integers $n$. For the basis step, we are told that $P(1)$ is true. For the inductive step, we are told that $P(k)$ implies $P(k+1)$ for each $k \ge 1$. Therefore by the principle of mathematical induction, $P(n)$ is true for all positive integers $n$.