---
title: Creative Uses of Induction
description: 
published: true
date: 2021-04-27T18:29:23.923Z
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