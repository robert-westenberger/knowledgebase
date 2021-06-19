---
title: Parallel Task Scheduling
description: 
published: true
date: 2021-06-19T21:46:39.700Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Parallel Task Scheduling
For a set of tasks with dependencies (some tasks may only be begun after some other tasks are completed), [topological sorting](/mathematics/discrete-mathematics/partial-orderings) provides a way to execute tasks sequentially while respecting dependencies.

If the tasks are programs and we have a machine that is capable of executing programs in parallel, then how should we schedule the tasks in order to minimize the total time to complete all tasks? We can use walk relations on acyclic graphs. 

## Chains
A **chain** in a DAG (Directed Acyclic Graph) is a set of vertices such that any two of them are **comparable** (when one is reachable from the other).