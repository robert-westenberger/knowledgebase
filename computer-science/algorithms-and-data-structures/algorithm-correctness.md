---
title: Algorithm Correctness
description: 
published: true
date: 2021-07-05T20:42:18.724Z
tags: algorithms
editor: markdown
---

# Robot Tour Optimization (Travelling Salesman)
We want to minimize the **tour** (or **cycle**) of a robotic arm that is soldering computer chips onto a substrate. Each cycle, the robot arm solders a bunch of contact points in order. 

Assume that the robot arm moves with a fixed speed, so the time to travel between two points is proportional to their distance.

**Problem**: Robot Tour Optimization 
**Input:** A set $S$ of $n$ points in the plane. 
**Output:** What is the shortest cycle tour that visits each point in the set $S$ ?

This is just the traveling salesman problem in disguise.

There is a fundamental difference between **algorithms**, procedures that always produce a correct result, and **heuristics**, which may usually do a good job but provide no guarantee of correctness.

# Scheduling 
What would be the optimal way to $n$ schedule jobs, where you can only do one job at a time, and you must complete the entirety of the job before moving onto another. 


**Problem:** Movie Scheduling Problem
**Input:** A set $I$ of $n$ intervals on the line.
**Output:** What is the largest subset of mutually non-overlapping intervals that can be selected from $I$?



## Algorithm

```
OptimalScheduling(I)
	While (I ≠ ∅) do
		Accept the job j from I with the earliest completion date.
		Delete j, and any interval which intersects j, from I.
```

**Note:** Topological sorting (of [Partial Orderings](/mathematics/discrete-mathematics/partial-orderings)) can be used to find the optimal scheduling for a set of tasks).

# Reasoning about Correctness
Proofs are used to argue about the correctness of algorithms.

## Problems and Properties
We need a **problem specification:**
* The set of allowed input instances
* The required properties of the algorithm's output.
	* Should be well defined (e.g. the "best" route for the travelling saleman problem is ambiguous. Is "best" in this case the shortest, fastest, or the one minimizing the number of turns?).
  * The output / goals for an algorithm should be optimizing for a single goal. A goal like "Find the shortest route from a to b e that doesn't use more than twice as many turns as necessary" is complicated and difficult to reason about.

An important technique in algorithm design is to narrow the set of allowable instances until there is a correct and efficient algorithm. For example, a graph problem can be restricted down to trees. A geometric problem from two dimensions can be restricted down to 1 dimension.

## Demonstrating Incorrectness
### Counterexamples
Provide **counterexamples** (an instance on which an algorithm yields an incorrect answer) to prove an algorithm is incorrect.

#### Properties of Good Counterexamples
Good counterexamples are
* Verifiable - You must be able to
	* Calculate what answer your algorithm will give in this instance
  * Display a better answer so as to prove that the algorithm didn't find it. 
* Simple - Once a counterexample is found, strip all unneccessary details away that don't relate to showing why the proposed algorithm fails.

#### Techniques for Finding Good Counterexamples
* **Think small**
	* Try to find small examples on which an algorithm fails, because they are easier to verify and reason about.
* **Think exhaustively** 
* **Hunt for the weakness**
* **Go for a tie**
* **Seek extremes**
	