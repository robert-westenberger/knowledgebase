---
title: Creative Uses of Induction
description: 
published: true
date: 2021-04-27T18:48:02.143Z
tags: discrete-mathematics
editor: markdown
---

# Tiling a checkerboard with triominoes
A *trionimo* (alternately *tromino*) is made up of three attached squares, which can be of two types: ![trionimoes.png](/trionimoes.png)


**Theorem:** For any integer $n \ge 1$, if one square is removed from a $2^n \times 2^n$ checkerboard, the remaining squares can be completely covered by L-shaped trionimoes.

The main insight leading to a proof of this theorem is the observation that because $2^{k+1}=2 \cdot 2^{k}$, when a $2^{k+1} \times 2^{k+1}$ board is is split in half both vertically and horizontally, each half side will have length $2^k$ and so each resulting quadrant will be a $2^{k} \times 2^{k}$ checkerboard. 

**Proof**:
We use induction. Let $P(n)$ be the sentence
$$
\text {If any square is removed from a} \medspace 2^n \times 2^n \medspace \text{checkerboard, then the} \medspace \\ \text {remaining squares can be completely coverd by L-shaped trominoes.}
$$

**Base Case:** $P(1)$ is a $2^1 \times 2^1$ checkerboard, which is just $4$ squares. If one square is removed, the rest form an L shaped trionimo which completely covers the rest of the checkerboard. 

**Inductive Step:** We aim to prove that if $P(k) \rarr P(k+1)$ is $P(k)$ is true. 

Let $P(k)$ be the sentence
$$
\text {If any square is removed from a} \medspace 2^k \times 2^k \medspace \text{checkerboard, then the} \medspace \\ \text {remaining squares can be completely coverd by L-shaped trominoes.}
$$

Let $P(k+1)$ be the sentence
$$
\text {If any square is removed from a} \medspace 2^k+1 \times 2^k+1 \medspace \text{checkerboard, then the} \medspace \\ \text {remaining squares can be completely coverd by L-shaped trominoes.}
$$

Consider a $2^{k+1} \times 2^{k+1}$ checkerboard with one square removed. Divide it into four equal quadrants. Each will consist of a $2^k \times 2^k$ checkerboard.
![checkerboard.png](/checkerboard.png)

In one of the quadrants, one square will have been removed, and so by the inductive hypothesis, all the remaining squares in this quadrant can be completely covered by L-shaped trionimoes.

The other three quadrants meet at the center of the checkerboard. The center of the checkerboard serves as a corner of a square from each of those quadrants. An L-shaped trionimo can be placed on those three central squares (illustrated above).

By inductive hypothesis, the remaining squares in each of the three quadrants can be completely covered by L-shaped trionimoes. Thus every square in the $2^{k+1} \times 2^{k+1}$ checkerboard except the one that aws removed can be compeltely covered by L-shaped trionimoes.
