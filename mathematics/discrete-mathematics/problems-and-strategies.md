---
title: Problems and Strategies
description: 
published: true
date: 2021-04-06T18:14:55.510Z
tags: discrete-mathematics
editor: markdown
---

# Problems and Strategies
## Determine whether compound proposition is satisfiable
Keep plugging in truth values for the propositional variables until you find variables that make the proposition true. We only need to find one case in order for a proposition to be satisfiable. 

We don't have to blindly plug in truth values - we can reason about the different propositions in the compound proposition. 

## Express English language statements using mathematical and logical operators, predicates, quantifiers
Rewrite the given statement so that the implied quantifiers and a domain are shown (if it isn't already). Then, introduce variables to the stateement. 

So "The sum of two positive integers is always positive" becomes "For every two integers, if these integers are both positive, then the sum of these integers is positive" and then that becomes "For all positive integers $x$ and $y$, $x + y$ is positive." In logic notation this is $\forall x \forall y((x>0) \wedge(y>0) \rightarrow(x+y>0))$.

We could also translate the above example using positive integers as the domain. Then the statement becomes For every two positive integers, the sum of these integers is positive. which is $\forall x \forall y(x+y>0)$.
