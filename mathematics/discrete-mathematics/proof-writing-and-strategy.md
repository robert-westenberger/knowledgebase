---
title: Proof Writing and Strategy
description: 
published: true
date: 2021-04-02T17:56:45.264Z
tags: discrete-mathematics
editor: markdown
---

# Forward and Backward Reasoning
**Forward reasoning** is starting with the premises, and using the premises together with axioms and known theorems to take a sequence of logically connected steps to lead to a conclusion (for a direct proof). Similarly, with indirect reasoning you can start with the negation of the conclusion and obtain the negation of the premises.

**Backward reasoning** to prove a statement $q$ is to find a statement $p$ that we can use to prove $p \rarr q$.

## Examples of Backward Reasoning
### Example 1
Given two positive real numbers $x$ and $y$, their arithmetic mean is $(x+y) / 2$ and their geometric mean is $\sqrt{x y}$. When comparing the arithmetic and geometric means of pairs of distinct positive real numbers, we find that the arithmetic mean is always greater than the geometric mean. Can we prove this inequality is always true?

To prove that $(x+y) / 2>\sqrt{x y}$ when $x$ and $y$ are distinct positive real numbers, we can work backward. We construct a sequence of equivalent inequalities. The equivalent inequalities are 
$$
\begin{aligned}
(x+y) / 2 &>\sqrt{x y} \\
(x+y)^{2} / 4 &>x y \\
(x+y)^{2} &>4 x y \\
x^{2}+2 x y+y^{2} &>4 x y \\
x^{2}-2 x y+y^{2} &>0 \\
(x-y)^{2} &>0
\end{aligned}
$$

Because $(x-y)^{2}>0$ when $x \ne y$, it follows that the final inequality is true. Because all the inequalities are equivalent, it follows that $(x+y) / 2>\sqrt{x y}$ when $x \ne y$. Once we have carried out this backward reasoning, we can build a proof based on reversing the steps (into forward reasoning) (Note that the steps of our backward reasoning will
not be part of the final proof. These steps serve as our guide for putting this proof together.)

**Proof**: Suppose that x and y are distinct positive real numbers. Then $(x − y)^2 \gt 0$ because the square of a nonzero real number is positive (see Appendix 1). Because $(x − y)^2 = x^2 − 2xy + y^2$, this implies that $x^2 − 2xy + y^2 \gt 0$. Adding $4xy$ to both sides, we obtain $x^2 + 2xy + y^2 \gt 4xy$. Because $x^2 + 2xy + y^2 = (x + y)^2$, this means that $(x + y)^2 \ge 4xy$. Dividing both sides of this equation by $4$, we see that $(x + y)^2∕4 \gt xy$. Finally, taking square roots of both sides (which preserves the inequality because both sides are positive) yields $(x + y)∕2 > \sqrt{xy}$. We conclude that if x and y are distinct positive real numbers, then their arithmetic mean $(x + y)∕2$ is greater than their geometric mean $\sqrt{xy}$.