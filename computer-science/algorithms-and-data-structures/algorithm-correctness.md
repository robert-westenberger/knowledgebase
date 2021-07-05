---
title: Algorithm Correctness
description: 
published: true
date: 2021-07-05T19:03:52.619Z
tags: algorithms
editor: markdown
---

# Robot Tour Optimization
We want to minimize the **tour** (or **cycle**) of a robotic arm that is soldering computer chips onto a substrate. Each cycle, the robot arm solders a bunch of contact points in order. 

Assume that the robot arm moves with a fixed speed, so the time to travel between two points is proportional to their distance.

**Problem**: Robot Tour Optimization 
**Input:** A set $S$ of $n$ points in the plane. 
**Output:** What is the shortest cycle tour that visits each point in the set $S$ ?

This is just the traveling salesman problem in disguise.

There is a fundamental difference between **algorithms**, procedures that always produce a correct result, and **heuristics**, which may usually do a good job but provide no guarantee of correctness.

# Selecting the Right Jobs