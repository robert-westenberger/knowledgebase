---
title: Propositional Logic
description: 
published: true
date: 2021-02-25T17:37:58.656Z
tags: computer-science, mathematics, discrete-mathematics
editor: markdown
---

# Propositional Logic

## Propositions
A statement that is either true or false. 

A proposition is **atomic** if it cannot be broken down into smaller statements / propositions. Otherwise, it is called **molecular**. 

## Predicates
A proposition whose truth depeonds on the value of one or more variables. "n is a perfect square" is a predicate, since you don't know its true or false until a value for n is provided.

## Logical Connectives
$$
\begin{array}{cc}
\text { Symbol } & \text { Meaning } \\
\hline \vee & \text { or } \\
\wedge & \text { and } \\
\rarr & \text { implication (or conditional) } \\
\leftrightarrow & \text { biconditional } \\
\neg & \text { not }
\end{array}
$$

$P \vee Q$ is read "P or Q"
$P \wedge Q$ is read "P and Q"
$P \rarr Q$ is read "if P then Q"
$P \leftrightarrow Q$ is read "P if and only if Q"
$\neg P$ is read "not P"

Note that the OR is the **inclusive or** and that $P \vee Q$ is true when both P and Q are true.
## Truth Conditions for Connectives

$P \vee Q$ is true when P or Q or both are true
$P \wedge Q$ is true when both P and Q are true
$P \rarr Q$ is true when P is false or Q is true or both
$P \leftrightarrow Q$ is true when P and Q are both true, or both false.
$\neg P$ is true when P is false.

## Truth Conditions for Connectives