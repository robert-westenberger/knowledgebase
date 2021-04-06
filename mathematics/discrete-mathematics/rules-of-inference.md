---
title: Rules of Inference
description: 
published: true
date: 2021-04-06T19:00:27.395Z
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

## Rules of Inference for Quantified Statements
### Universal Instantiation
$$\therefore \frac{\forall x P(x)}{P(c)}$$
### Universal Generalization
$$
\therefore \frac{P(c) \text { for an arbitrary } c}{\forall x P(x)}
$$
### Existential Instantiation
### Existential Generalization

## Using Rules of Inference to Build Arguments
Rules of inference can be used to deduce new statements from the statements whose truth that we already know. 
Below is an example of showing the premises "It is not sunny this afternoon and it is colder than yesterday." "We will go swimming only if it is sunny" "If we do not go swimming, then we will take a canoe trip" "If we take a canoe trip, then we will be home by sunset" leads to the conclusion "We will be home by sunset".

Let $p$ be the proposition “It is sunny this afternoon,” $q$ the proposition “It is colder Extra Examples than yesterday,” $r$ the proposition “We will go swimming,” $s$ the proposition “We will take a canoe trip,” and $t$ the proposition “We will be home by sunset.”

Step
1. $\neg p \wedge q$ (Premise)
2. $\neg p$ (Simplification using 1)
3. $r \rightarrow p$ (Premise)
4. $\neg r$ (Modus tollens using (2) and (3))
5. $\neg r \rightarrow s$ (Premise)
6. $s$ (Modus ponens using (4) and (5))
7. $s \rightarrow t$ (Premise)
8. $t$ (Modus ponens using (6) and (7))


