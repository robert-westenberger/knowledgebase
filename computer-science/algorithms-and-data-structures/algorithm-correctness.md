---
title: Algorithm Correctness
description: 
published: true
date: 2021-07-05T20:11:23.369Z
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

Topological sorting (of [Partial Orderings](/mathematics/discrete-mathematics/partial-orderings)) can be used to find the optimal scheduling for a set of tasks).

## Algorithm

```
OptimalScheduling(I)
	While (I ≠ ∅) do
		Accept the job j from I with the earliest completion date.
		Delete j, and any interval which intersects j, from I.
```