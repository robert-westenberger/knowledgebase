---
title: Parallel Task Scheduling
description: 
published: true
date: 2021-06-19T22:18:22.045Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Parallel Task Scheduling
For a set of tasks with dependencies (some tasks may only be begun after some other tasks are completed), [topological sorting](/mathematics/discrete-mathematics/partial-orderings) provides a way to execute tasks sequentially while respecting dependencies.

If the tasks are programs and we have a machine that is capable of executing programs in parallel, then how should we schedule the tasks in order to minimize the total time to complete all tasks? We can use walk relations on acyclic graphs. 

## Chains
A **chain** in a DAG (Directed Acyclic Graph) is a set of vertices such that any two of them are **comparable** (when one is reachable from the other). A vertex in a chain that is reachable from all other vertices in the chain is called a **maximum element** of the chain. A finite chain is said to **end at** its maximum element.


## Minimum Time to Schedule Tasks
The time it takes to schedule tasks is at least as large as the number of vertices in any chain (because if we used less time than the size of some chain, then two items from the chain would have to be done at the same step, contradicting the precedence constraints). A largest chain is also known as a **critical path**. 

## Schedules
All tasks can be scheduled in $t$ steps, where $t$ is the size of the largest chain. This is true for any DAG. A **schedule** for performing tasks specifies which tasks to do at successive steps. Every task $a$ has to be scheduled at some step, and all the tasks have to be completed before task $a$ must be scheduled for an earlier step. 

A **partition** of a set $A$ is a set of nonempty subsets of $A$ called the **blocks** of the partition, such that every element of $A$ is in exactly one block.
For example, one possible partition of the set $\{a, b, c, d, e\}$ into three blocks is
$$
\{a, c\} \quad\{b, e\} \quad\{d\}
$$

A **parallel schedule** for a DAG $D$ is a partition of $V(D)$ into blocks $A_{0}, A_{1}, \ldots$, such that when $j<k$, no vertex in $A_{j}$ is reachable from any vertex in $A_{k} .$ The block $A_{k}$ is called the set of elements **scheduled at step** $k$, and the **time** of the schedule is the number of blocks. The maximum number of elements scheduled at any step is called the **number of processors** required by the schedule.

A **largest** chain ending at an element $a$ is called a **critical path to** $a$. The number of elements less than $a$ in the chain is called the **depth of** $a$. So in any possible parallel schedule, there must be at least depth $(a)$ steps before task $a$ can be started. In particular, the minimal elements are precisely the elements with depth $0$.