---
title: Propositional Logic
description: 
published: true
date: 2021-02-25T18:22:32.706Z
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

## Implications
$P \rarr Q$  "if P then Q". Often rephrased as $P \text { IMPLIES } Q$.

P is the **hypothesis** (or **antecedent**)
Q is the **conclusion** (or **consequent**)

An implication is true provided P is false or Q is true (or both), and false otherwise. In particular, the only way for P → Q to be false is for P to be true and Q to be false.

* Quadratic Formula - If $ax^2 + bx + c = 0 \medspace \text{and} \medspace a \not = \text{, then} \medspace x=\left(-b \pm \sqrt{b^{2}-4 a c}\right) / 2 a$.

### Converse and Contrapositive
The **converse** of an implication $P \rarr Q$ is the implication $Q \rarr P$.
The **contrapositive** of an implication $P \rarr Q$ is the statement $\neg Q \rarr \neg P$. An implication and its contrapositive are logically equivalent.


#### Proof Method #1 
In order to prove $P \text { IMPLIES } Q$: 
1) Write, "Assume P".
2) Show that Q logically follows. 

##### Example 1 of Proof Method #1

**Theorem:** $\text { If } 0 \leq x \leq 2 \text { , then }-x^{3}+4 x+1>0$

**Scratchwork:** We can factor $-x^3 + 4x$ to get $-x^3 + 4x = x(2-x)(2+x)$ .For $x$ between 0 and 2, all the terms on the right side are nonnegative. We can organize our observations into a formal proof.

**Proof:** Assume $0 \leq x \leq 2$. Then, $x$, $2-x$, and $2+x$ are all nonnegative. Therefore, the product of these terms is also nonnegative. Adding 1 to this product gives a positive number, so:
$$x(2-x)(2+x)+1>0$$
Multiplying out on the left side proves that 
$$
-x^{3}+4 x+1>0
$$ 
as claimed. $\blacksquare$

Note: Proofs typically begin with the word "Proof" and end with some sort of delimiter like $\square$, $\blacksquare$, or "QED".
##### Example 2 of Method #1
**Theorem:** If two numbers $a$ and $b$ are even, then their sum $a + b$ is even.
**Proof:** Assume the numbers $a$ and $b$ are even. This means that $a = 2k$ and $b=2j$ for some integers $j$ and $k$. The sum is then $a+b=2k+2j=2(k+j)$. Since $k+j$ is an integer, this means that $a+b$ is even. $\blacksquare$

Notice we just assume P is true and repeatedly ask and answer the question, "What does that mean?". Eventually we conclude that it means the conclusion.

