---
title: Rules of Inference
description: 
published: true
date: 2021-03-30T18:29:25.428Z
tags: discrete-mathematics
editor: markdown
---

# Rules of Inference

An **argument** is a sequence of statements that end with a conclusion. 

A **valid** argument is one where the conclusion, or final statement of the argument, follows from the truth of the preceding statements, or **premises**.

An argument is in **argument form** when it's propositions are changed to propositional variables. An argument form is valid no matter which particular propositions are subsituted for the propositional variables in its premises, the conclusion is true if the premises are all true. 

## Rules of Inference for Propositional Logic

The tautology $(p \wedge(p \rightarrow q)) \rightarrow q$ is the basis of the rule of inference called **modus ponens** or the **law of detachment**. This tautology leads to the following valid argument form (remember $\therefore$ means "therefore").

$$
\begin{aligned}
& p \\
& p \rightarrow q \\
\hline \therefore q 
\end{aligned}
$$

Modus ponens tells us that if a conditional statement and the hypothesis of this conditional statement are both true, then the conclusion must also be true. 