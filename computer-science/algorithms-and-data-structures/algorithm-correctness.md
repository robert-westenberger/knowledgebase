---
title: Algorithm Correctness
description: 
published: true
date: 2021-07-05T21:43:32.558Z
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
	* If a proposed algorithm is of the form “always take the biggest” (better known as the greedy algorithm), think about why that might prove to be the wrong thing to do
* **Go for a tie** 
	* In the example of breaking a greedy heuristic, provide an instance where everything is the same size.
* **Seek extremes** 
	* It is usually easier to verify or reason about extreme examples than more muddled ones.
  
## Induction and Recursion
### Example
```
Increment(y)
	if (y = 0) then return(1) else
		if (y mod 2) = 1 then
			return(2 · Increment(Math.floor(y/2)))
		else return(y + 1)
```

The base case of $y=0$ is obviously handled. 

Assume the function works correctly for the general case of $y=n-1$. Given this, we must demonstrate the truth for the case of $y=n$. The cases corresponding to even numbers are obvious, because $y+1$ is explicitly returned when $(y \operatorname{mod}2)=0$.

For odd numbers, the answer depends on what Increment(Math.floor(y/2)) returns. Our inductive assumption ($y=n-1$) doesn't support values that are about half. We can fix this by strengthening our assumption to declare the genral case holds for all $y \leq n-1$.

Now the case of the odd $y$ (i.e. $y=2 m+1$ for some integer $m$):

$$
\begin{aligned}
2 \cdot \operatorname{Increment}(\lfloor(2 m+1) / 2\rfloor) &=2 \cdot \operatorname{Increment}(\lfloor m+1 / 2\rfloor) \\
&=2 \cdot \operatorname{Increment}(m) \\
&=2(m+1) \\
&=2 m+2=y+1
\end{aligned}
$$
and the general case is resolved $\blacksquare$.
(Note: Math.floor(x) = $\lfloor x \rfloor$)

## Modeling the Problem
Most algorithms are designed to work on rigorously defined abstract struvtures such as **permutations**, **graphs**, and **sets**.