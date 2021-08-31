---
title: Logarithm Identity Proofs
description: 
published: true
date: 2021-08-31T18:43:44.279Z
tags: mathematics, proof-writing
editor: markdown
---

# Product Rule
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

# Power Rule
$\log _{a} x^{y}=y \log _{a} x$

Assume $\mathrm{m}=\log _{\mathrm{a}} \mathrm{x}$.

Write $m$ in exponent form, so $\mathrm{x}=\mathrm{a}^{\mathrm{m}}$.

Raise both sides by the power of $y$.
$\mathrm{x}^{\mathrm{y}}=\left(\mathrm{a}^{\mathrm{m}}\right)^{\mathrm{y}}$

Convert back to logarithmic form
$\log _{a} x^{y}=m y$

Substitute $m$ from our initial assumption.

$\log _{a} x^{y}=y \log _{a} x$
# Change of Base Rule
$\log _{a} x=\frac{\log _{b} x}{\log _{b} a}$

Assume $\mathrm{x}=\log _{\mathrm{a}} \mathrm{x}$, which is $a^x = x$ in exponent form.

Now take $log_b$ of both sides.

$\log _{b} a^{x}=\log _{b} x$
$x \log _{b} a=\log _{b} x$
$x=\frac{\log _{b} x}{\log _{b} a}$

# $x^{\log _{b} y}=y^{\log _{b} x}$

The log to the base $b$ of $x$ is defined as the number which, when $b$ is raised to this number, gives back $x$. 

Since $x=b^{\log _{b}(x)}$ that means $x^{\log _{b}(y)}=\left(b^{\log _{b}(x)}\right)^{\log _{b}(y)}$.

Applying the rule of exponents which is that $\left(s^{r}\right)^{t}=s^{r t}$, we get $\left(b^{\log _{b}(x)}\right)^{\log _{b}(y)}=b^{\log _{b}(x) \log _{b}(y)}$.

Put all together, 

$$
x^{\log _{b}(y)}=b^{\log _{b}(x) \log _{b}(y)}=b^{\log _{b}(y) \log _{b}(x)}=y^{\log _{b}(x)}
$$

# $\lceil\lg (n+1)\rceil=\lfloor\lg n\rfloor+1$
(used the base 10 log here)
To prove $\lceil\lg (n+1)\rceil=\lfloor\lg n\rfloor+1$, we need to consider the following four cases:

**Case 1:** $x=1$
**Case 2:** $x=2^k$ for some values $k \ge 1$

**Case 3:** $2^k \lt x \lt 2^{k+1} - 1$ for some $k \ge 2$.

**Case 4:** $x = 2^k -1$ for some $k \ge 2$.


Assuming the fact that $k<y<k+1$, then $\lfloor y\rfloor=k$ and $\lceil y\rceil=k+1$.

**Case 1:** $\lceil\lg (x+1)\rceil=\lceil\lg 2\rceil=\lceil 1\rceil$. 
**Case 2:** $\lceil\lg (2^4+1)\rceil= 2 = \lfloor\lg 2^4\rfloor+1 = 2$
**Case 3:** $\lceil\lg (9+1)\rceil= 2 = \lfloor\lg 9\rfloor+1 = 2$
**Case 4:** $\lceil\lg (7+1)\rceil= 1 = \lfloor\lg 7\rfloor+1 = 1$
