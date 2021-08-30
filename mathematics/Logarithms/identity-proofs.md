---
title: Logarithm Identity Proofs
description: 
published: true
date: 2021-08-30T18:23:09.599Z
tags: mathematics, proof-writing
editor: markdown
---

# Product Rule Proof
$\log _{a}(x y)=\log _{a} x+\log _{a} y$

Assume $\mathrm{m}=\log _{\mathrm{a}} \mathrm{x}$ and $\mathrm{n}=\log _{\mathrm{a}} \mathrm{y}$.

Writing the above in exponent form, we get $x=a^m$ and $y=a^n$.

Multiplying $x$ and $y$ results in $a^m \cdot a^n = a^{m+n}$.

Taking the log of both sides..

$$
\begin{aligned}
&\log _{a} x y=\log _{a} a^{n+n} \\
&\log _{a} x y=(m+n) \log _{a} a \\
&\log _{a} x y=m+n
\end{aligned}
$$

Substituting the values of $m$ and $n$ from our initial assumption:
$$
\log _{a} x y=\log _{a} x+\log _{a} y
$$