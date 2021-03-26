---
title: Propositional Logic
description: 
published: true
date: 2021-03-26T02:14:25.521Z
tags: computer-science, mathematics, discrete-mathematics
editor: markdown
---

# Propositional Logic

## Propositions
A statement that is either true or false. 

A proposition is **atomic** if it cannot be broken down into smaller statements / propositions. Otherwise, it is called **molecular**. 


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

## Negation
Note that the notation for negation isn't standardized. $\neg p$ and $\bar{p}$ are the most common, you might also see $\sim p$, $-p$, $p^{\prime}$, $Np$, and $!p$

The negation of the English sentence "Bob’s smartphone has at least 32 GB of memory” is “Bob’s smartphone does not have at least 32 GB of memory”. This could be rewritten more simply as "Bob's cellphone has less than 32 GB of memory."

Note how in this specific case, "greater than or equal to 32 GB" becomes "less than 32GB" so we go from $\ge$ to $\lt$


## Implications
$P \rarr Q$  "if P then Q". Often rephrased as $P \text { IMPLIES } Q$.

P is the **hypothesis** (or **antecedent**)
Q is the **conclusion** (or **consequent**)

An implication is true provided P is false or Q is true (or both), and false otherwise. In particular, the only way for P → Q to be false is for P to be true and Q to be false.

* Quadratic Formula - If $ax^2 + bx + c = 0 \medspace \text{and} \medspace a \not = \text{, then} \medspace x=\left(-b \pm \sqrt{b^{2}-4 a c}\right) / 2 a$.

### Converse Inverse, and Contrapositive
The **converse** of an implication $P \rarr Q$ is the implication $Q \rarr P$. An example of a true implication and a false converse woul be, "If a shape is a square, then it is a rectangle". Or, "If a number greater than 2 is prime, then that number is odd" (Just because a number is odd does not mean it is prime). 

There can be implications that's converse is also true. For example, the pythagorean theorem has a true converse. Is $a^2 + b^2 = c^2$, then the triangle with sides a, b, and c is a right triangle.


The **contrapositive** of an implication $P \rarr Q$ is the statement $\neg Q \rarr \neg P$. An implication and its contrapositive are logically equivalent. The contrapositive can be helpful in deciding whether an implication is true: often it is easier to analyze the contrapositive.

If an implication and its converse are true, we say that P and Q are equivalent and write $P \leftrightarrow Q$ ( the biconditional).

The **inverse** of a proposition $P \rarr Q$ is $\neg P \rarr \neg Q$
### If and only if
$P \leftrightarrow Q$ is logically equivalent to $(P \rarr Q) \wedge (Q \rarr P)$.

Example: Given an integer $n$, it is true that $n$ is even if and only if $n^2$ is even. That is, if $n$ is even, then $n^2$ is even, as well as the converse: if $n^2$ is even, then $n$ is even.

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

### Logic and Bit Operations
Computer **bit operations** correspond to the logical connectives. 
Below is a table for the bit operators OR ($\vee$)
$$
\begin{array}{c|c|c|c|c}
 &  & OR & AND & XOR \\
\boldsymbol{x} & \boldsymbol{y} & \boldsymbol{x} \vee \boldsymbol{y} & \boldsymbol{x} \wedge \boldsymbol{y} & \boldsymbol{x} \oplus \boldsymbol{y} \\
\hline 0 & 0 & 0 & 0 & 0 \\
0 & 1 & 1 & 0 & 1 \\
1 & 0 & 1 & 0 & 1 \\
1 & 1 & 1 & 1 & 0
\end{array}
$$
# Applications of Propositional
Propositional logic and its rules can be used to design computer circuits, to construct computer programs, to verify the correctness of those programs, and to solve many familiar puzzles. Software systems based on the rules of logic have been developed for constructing some, but not all, types of proofs automatically

## Translating English Sentences
“You cannot ride the roller coaster if you are under 4 feet tall unless you are older than 16 years old., where 

$q$ "You can ride the roller coaster"
$r$ "You are under 4 feet tall"
$s$ "You are older than 16 years old"

$$
(r \wedge \neg s) \rightarrow \neg q
$$
(There are other ways to represent this sentence)
## Boolean Searches
## Logic Puzzles
## Logic Circuits

# Propositional Equivalences
A compound proposition that is always true, no matter the truth values of the propositional variables that occur in it, is a **tautology**. A compound proposition that is always false is a **contradiction**.

## De Morgans Laws
$$
\begin{array}{l}
\neg(p \wedge q) \equiv \neg p \vee \neg q \\
\neg(p \vee q) \equiv \neg p \wedge \neg q
\end{array}
$$

De Morgan's laws for negating conjunctions and disjunctions.
## Conditional-Disjunction Equivalence
$p \rarr q$ and $\neg p \vee q$ are logically equivalent.
$$
\begin{array}{cc|c|c|c}
\boldsymbol{p} & \boldsymbol{q} & \neg \boldsymbol{p} & \neg \boldsymbol{p} \vee \boldsymbol{q} & \boldsymbol{p} \rightarrow \boldsymbol{q} \\
\hline \mathrm{T} & \mathrm{T} & \mathrm{F} & \mathrm{T} & \mathrm{T} \\
\mathrm{T} & \mathrm{F} & \mathrm{F} & \mathrm{F} & \mathrm{F} \\
\mathrm{F} & \mathrm{T} & \mathrm{T} & \mathrm{T} & \mathrm{T} \\
\mathrm{F} & \mathrm{F} & \mathrm{T} & \mathrm{T} & \mathrm{T}
\end{array}
$$

## Constructing New Logical Equivalences
Below, we show that $\neg(p \rightarrow q)$ and $p \wedge \neg q$ are logically equivalent. 
$$
\begin{aligned}
\neg(p \rightarrow q) & \equiv \neg(\neg p \vee q) & \text {conditional-disjunction equivalence} \\
& \equiv \neg(\neg p) \wedge \neg q & \text {De Morgan law} \\
& \equiv p \wedge \neg q & \text {double negation law}
\end{aligned}
$$

Another example, we show that $\neg(p \vee(\neg p \wedge q))$ and $\neg p \wedge \neg q$ are logically equivalent by developing a series of logical equivalences.
$$
\begin{aligned}
\neg(p \vee(\neg p \wedge q)) & \equiv \neg p \wedge \neg(\neg p \wedge q) & \text {second De Morgan law} \\
& \equiv \neg p \wedge[\neg(\neg p) \vee \neg q] & \text {first De Morgan law} \\
& \equiv \neg p \wedge(p \vee \neg q) & \text {double negation law} \\
& \equiv (\neg p \wedge p) \vee(\neg p \wedge \neg q) & \text {second distributive law} \\
& \equiv \mathbf{F} \vee(\neg p \wedge \neg q) & \text {because} \neg p \wedge p \equiv \mathbf{F} \\
& \equiv (\neg p \wedge \neg q) \vee \mathbf{F} & \text {by the commutative law for disjunction} \\
& \equiv \neg p \wedge \neg q & \text {by the identity law for } \mathbf{F} \\
\end{aligned}
$$
## Satisfiability
