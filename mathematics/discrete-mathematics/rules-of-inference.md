---
title: Rules of Inference
description: 
published: true
date: 2021-03-31T17:40:11.707Z
tags: discrete-mathematics
editor: markdown
---

# Rules of Inference

An **argument** is a sequence of statements that end with a conclusion. 

A **valid** argument is one where the conclusion, or final statement of the argument, follows from the truth of the preceding statements, or **premises**.

An argument is in **argument form** when it's propositions are changed to propositional variables. An argument form is valid no matter which particular propositions are subsituted for the propositional variables in its premises, the conclusion is true if the premises are all true. 

## Rules of Inference for Propositional Logic
### Modus Ponens
The tautology $(p \wedge(p \rightarrow q)) \rightarrow q$ is the basis of the rule of inference called **modus ponens** or the **law of detachment**. This tautology leads to the following valid argument form (remember $\therefore$ means "therefore").

$$
\begin{aligned}
& p \\
& p \rightarrow q \\
\hline \therefore q 
\end{aligned}
$$

Modus ponens tells us that if a conditional statement and the hypothesis of this conditional statement are both true, then the conclusion must also be true. 
### Modus Tollens
The tautology $(\neg q \wedge(p \rightarrow q)) \rightarrow \neg p$
$$
\begin{aligned}
& \neg q \\
& p \rightarrow q \\
\hline \therefore \neg p 
\end{aligned}
$$
### Hypothetical Syllogism
$((p \rightarrow q) \wedge(q \rightarrow r)) \rightarrow(p \rightarrow r)$
$$
\begin{aligned}
& p \rightarrow q \\
& q \rightarrow r \\
\hline \therefore \medspace
& p \rightarrow r
\end{aligned}
$$
### Disjunctive Syllogism
$
((p \vee q) \wedge \neg p) \rightarrow q
$
$$
\begin{array}{l}
p \vee q \\
\neg p \\
\hline \therefore q
\end{array}
$$
### Addition
$$
p \rightarrow(p \vee q)
$$
$$
\frac{p}{\therefore p \vee q}
$$
### Simplification
$$
(p \wedge q) \rightarrow p
$$
$$
\frac{p \wedge q}{\therefore p}
$$
### Conjunction
$$
((p) \wedge(q)) \rightarrow(p \wedge q)
$$
$$
\begin{array}{l}
p \\
q \\
\hline \therefore p \wedge q
\end{array}
$$
### Resolution
$$
((p \vee q) \wedge(\neg p \vee r)) \rightarrow(q \vee r)
$$
$$
\begin{array}{l}
p \vee q \\
\neg p \vee r \\
\hline \therefore q \vee r
\end{array}
$$
## Using Rules of Inference to Build Arguments