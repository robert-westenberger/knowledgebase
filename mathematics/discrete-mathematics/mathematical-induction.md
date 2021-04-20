---
title: Mathematical Induction
description: 
published: true
date: 2021-04-20T18:16:47.965Z
tags: discrete-mathematics
editor: markdown
---

# Induction

Induction proofs have two parts.
1. Show that the statement holds for the positive integer $1$. (the **basis step**)
2. Show that the statement holds for the next larger integer. ($P(k) \rightarrow P(k+1)$ is true for all positive integers $k$, the **inductive step**).

Induction is based on the rule of inference that tells us that if $P(1)$ and $\forall k(P(k) \rightarrow P(k+1))$ are true for the domain of positive integers, then $\forall n P(n)$ is true.

Induction can be used only to prove results obtained some other way. It is not a tool for discovering formulae or theorems.

Expressed as a rule of inference, induction can be stated as
$$
(P(1) \wedge \forall k(P(k) \rightarrow P(k+1))) \rightarrow \forall n P(n)
$$

Mathmatical induction relies on the [Well Ordering Principle](/mathematics/discrete-mathematics/well-ordering-principle).

## Template for Proofs by Mathematical Induction
1. Express the statement that is to be proved in the form "for all $n \geq b, P(n)$", for a fixed integer $b$. For statements of the form "$P(n)$ for all positive integers $n$, let $b=1$.  For statements of the form "$P(n)$ for all nonnegative integters $n$", let $b=0$. For some statements of the form $P(n)$, such as inequalities, you may need to determine the appropriate value of $b$ by checking the truth tables of $P(n)$ for small values of $n$. 

2. Write out the words "Basis Step". Then show $P(b)$ is true, taking care that the correct value of $b$ is used. 

3. Write out the words "Inductive Step", and state the inductive hypothesis in the form, "Assume $P(k)$ is true for an arbitrary fixed integer $k \ge b$."

4. State what needs to be proved under the assumption that the inductive hypothesis is true. That is, write out what $P(k+1)$ says.

5. Prove the statement $P(k+1)$ making use of the assumption $P(k)$. Be sure that your proof is valid for all integers $k$ with $k \ge b$, taking care that the proof works for small values of $k$, including $k=b$.

6. Clearly identify the conclusion of the inductive step, such as by saying, "This completes the inductive step."

7. After completing the basis and inductive step, state the conclusion, "By mathematical induction, $P(n)$ is true for all integers $n$ with $n \ge b$. 

## Examples 

### Proving Summation Formulae
Keep in mind that induction can't be used to derive a summation formula. We must already have the formukla before we can attempt to prove it by induction.

#### Example 1
Show that if $n$ is a positive integer, then 
$$
1+2+\cdots+n=\frac{n(n+1)}{2}
$$

**Basis Step:** $P(1)$ is true because $1=\frac{1(1+1)}{2}$. 

**Inductive Step:** For the inductive hypothesis we assume that $P(k)$ holds for an arbitrary positive integer $k$. That is, we assume

$$
1+2+\cdots+k=\frac{k(k+1)}{2}
$$

Under this assumption, it must be shown that $P(k+1)$ is true, namely, that 
$$
1+2+\cdots+k+(k+1)=\frac{(k+1)[(k+1)+1]}{2}=\frac{(k+1)(k+2)}{2}
$$
is also true.

We now look ahead to see how we might be able to prove that $P(k + 1)$ holds under the assumption that $P(k)$ is true.We observe that the summation in the left-hand side of $P(k + 1)$ is
$k + 1$ more than the summation in the left-hand side of $P(k)$. Our strategy will be to add $k + 1$ to
both sides of the equation in $P(k)$ and simplify the result algebraically to complete the inductive step.

Returning to the inductive step of the proof, when we add $k+1$ to both sides of the equation $P(k)$, we obtain 

$$
\begin{aligned}
1+2+\cdots+k+(k+1) & \stackrel{\text { IH }}{=} \frac{k(k+1)}{2}+(k+1) \\
&=\frac{k(k+1)+2(k+1)}{2} \\
&=\frac{(k+1)(k+2)}{2} .
\end{aligned}
$$

The last equation shows that $P(k+1)$ is true udner the assumption that $P(k)$ is true. This completes the inductive step. 

We have completed the basis and the inductive step, so by mathematical induction we know that $P(n)$ is true for all positive integers $n$. That is, we have proven that $1+2+\cdots+n=n(n+1) / 2$ for all positive integers $n$.

#### Example 2
Conjecture a formula for the sum of the first n positive odd integers. Then prove your conjecture using mathematical induction.

The sums of the first $n$ positive integers for $n=1,2,3,4,5$ are $1=1$, $1+3=4$, $1+3+5=9$, $1+3+5+7=16$, $1+3+5+7+9=25$

From these values its reasonable to conjecture that our formula for the sum of the first $n$ positive integers is $1+3+5+\cdots+(2 n-1)=n^{2}$. 

Let $P(n)$ denote the proposition that the sum of the first $n$ odd positive integers is $n^2$. Conjecture is that $P(n)$ is true for all positive integers $n$.

**Basis Step:** $P(1)= 1^2$ = 1
**Inductive Step:** We must show that $P(k) \rightarrow P(k+1)$ is true for every positive integer $k$. To do this, we assume the inductive hypothesis ( that $P(k)$ is true for every positive integer $k$, that is,
$1+3+5+\cdots+(2 k-1)=k^{2}$ )

To show that $\forall k(P(k) \rightarrow P(k+1))$ is true, we must show that $P(k)$ is true, then $P(k+1)$ is true. Note that $P(k+1)$ is 
$$
1+3+5+\cdots+(2 k-1)+(2 k+1)=(k+1)^{2}
$$

We need to look for a way to use the inductive hypothesis to show that $P(k+1)$ is true. $1+3+5+\cdots+(2 k-1)+(2 k+1)$ is the sum of its first $k$ terms $1+3+5+\cdots+(2 k-1)$ and its last term $2k-1$. So we can use our inductive hypothesis to replace $1+3+5+\cdots+(2 k-1)$ by $k^2$.

Returning to the proof, we find that 
$$
\begin{aligned}
1+3+5+\cdots+(2 k-1)+(2 k+1) &=[1+3+\cdots+(2 k-1)]+(2 k+1) \\
& \stackrel{\mathrm{IH}}{=} k^{2}+(2 k+1) \\
&=k^{2}+2 k+1 \\
&=(k+1)^{2}
\end{aligned}
$$

This shows that $P(k+1)$ follows from $P(k)$. Note that we used the inductive hypothesis $P(k)$ in the second equality to replace the sum of the first $k$ odd positive integers by $k^2$.

We have now completed both the basis step and the inductive step. We have shown that $P(1)$ is true and the conditional statement $P(k) \rightarrow P(k+1)$ is true for all positive integers $k$. Consequently, by the principle of mathematical induction we can conclude that $P(n)$ is true for all positive integers $n$. That is, we know that $1+3+5+\cdots+(2 n-1)=n^{2}$ for all positive integers $n$.

### Proving Inequalities

#### Example 1 
Use mathematical induction to prove the inequality 
$$n<2^{n}$$
for all positive integers $n$.

Let $P(n)$ be the proposition that $n \lt 2^n$.

**Basis Step:** $P(1)$ is true, because $1<2^{1}=2$. This completes the basis step.

**Inductive Step:** We assume the inductive hypothesis $k \lt 2^k$ is true for some arbitrary integer $k$. To complete the inductive step, we need to show that if $P(k)$ is true, then $P(k+1)$, which is the statement that $k+1<2^{k+1}$ is true. That is, we need to show if $k<2^{k}$, then $k+1<2^{k+1}$. To show that this conditional statement is true for the positive integer $k$, we first add $1$ to both sides of $k \lt 2^k$, and then note that $1 \le 2^k$. This tells us that 

$$
k+1<2^{k}+1 \leq 2^{k}+2^{k}=2 \cdot 2^{k}=2^{k+1}
$$

This shows that $P(k+1)$ is true, namely that $k+1<2^{k+1}$, based on the assumption that $P(k)$ is true. 

Therefore, because we have completed both the basis step and the inductive step, by the principle of mathematical induction we have shown that $n \lt 2^n$ is true for all positive integers $n$.


### Proving Divisibility Results
### Proving Results About Sets
### Proving Results About Algorithms

### Courtyard Tiling

Picture a $2^n \times 2^n$ grid. 
![2n_x_2n_grid.png](/2n_x_2n_grid.png)

One of the central squares in the grid will be occupied by a statue(Let's call it Bob's statue, or **B**). In the special case $n=0$, the whole courtyard consists of a single central square; otherwise there are four central squares.

A complication is that the architect of this grid courtyard insists on only special L-shaped tiles are to be used. 

![l_tiles.png](/l_tiles.png)

A courtyard meeting these constrains exists, at least for $n=2$. 

![grid.png](/grid.png)

For larger values of $n$, is there a way to tile a $2^n \times 2^n$ courtyard with L-shaped tiles and a statue in the center? Let's try to prove that this is so. 

**Theorem 1:** For all $n\ge0$ there exists a tiling of a $2^n\times2^n$ courtyard with a Bob statue in a central square.
**Proof:** This proof is by induction. Let $P(n)$ be the proposition that for every location of Bob in a $2^n \times 2^n$ courtyard, there exists a tiling of the remainder. 
**Base Case:**$P(0)$ is true because Bob fits the whole courtyard.
**Inductive Step:** Assume that $P(n)$ is true for some $n \ge 0$; that is, for every location of Bob in a $2^n \times 2^n$ courtyard, there exists a tiling of the remainder. Divide the $2^{n+1} \times 2^{n+1}$ courtyard into four quadrants, each $2^n \times 2^n$. One quadrant contains Bob (**B** in the diagram). Place a temporary Bob (**X** in the diagram) in each of the three central squares lying outside this quadrant:
![grid_placement_example.png](/grid_placement_example.png)

Now we can tile each of the four quadrants by the induction assumption. Replacing the three temporary Bobs with a single L-shaped tile completes the job. This proves that $P(n) \rarr P(n+1)$ for all $n \ge 0$. The theorem follows as a special case. $\blacksquare$


# Strong Induction