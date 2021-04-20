---
title: Mathematical Induction
description: 
published: true
date: 2021-04-20T19:19:17.953Z
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
#### Example
Use mathematical induction to prove that $7^{n+2}+8^{2 n+1}$ is divisible by $57$ for every nonnegative integer $n$. 

Let $P(n)$ denote the proposition "$7^{n+2}+8^{2 n+1}$ is divisible by $57$"

**Base Case:** $P(0)=7^{0+2}+8^{2 \cdot 0+1}=7^{2}+8^{1}=57$ is divisible by $57$.

**Inductive Step:** We assume $P(k)$ is true for an arbitrary nonnegative integer $k$, that is, we assume $7^{k+2}+8^{2 k+1}$ is divisible by $57$. 

We aim to prove $P(k) \rarr P(k+1)$, where $P(k+1)$ is the statement that $7^{(k+1)+2}+8^{2(k+1)+1}$ is divisible by $57$. 

$$
\begin{aligned}
7^{(k+1)+2}+8^{2(k+1)+1} &=7^{k+3}+8^{2 k+3} \\
&=7 \cdot 7^{k+2}+8^{2} \cdot 8^{2 k+1} \\
&=7 \cdot 7^{k+2}+64 \cdot 8^{2 k+1} \\
&=7\left(7^{k+2}+8^{2 k+1}\right)+57 \cdot 8^{2 k+1}
\end{aligned}
$$
We can now use the inductive hypothesis, which states that $7^{k+2}+8^{2 k+1}$ is divisible by $57$. We will use the following theorems for the rest of the proof: 

* **(i)** if $a \mid b$ and $a \mid c$, then $a \mid(b+c)$
* **(ii)** if $a \mid b$, then $a \mid b c$ for all integers

By **ii** and the inductive hypothesis, we conclude that the first term in the last sum, $7\left(7^{k+2}+8^{2 k+1}\right)$, is divisible by $57$. By **ii**, the second term, $57 \cdot 8^{2 k+1}$, is divisible by $57$. By part **i**, we conclude that  $7\left(7^{k+2}+8^{2 k+1}\right)+57 \cdot 8^{2 k+1}=7^{k+3}+8^{2 k+3}$ is divisible by $57$. This completes the inductive step. 

Because we have completed the base and inductive steps, by mathemtical induction we know that $7^{n+2}+8^{2 n+1}$ is divisible by $57$ for every nonnegative integer $n$.

### Proving Results About Sets
### Proving Results About Algorithms
#### Examples
##### Proving a greedy algorithm always produces an optimal solution
Consider an algorithm to schedule talks that have preset start and end times. The algorithm schedules as many talks as possible in a lecture hall, under the assumption that once a talk starts, it continues until it ends, and only one talk can proceed at a time. A talk can begin at the same time another one ends. 

The input of the algorithm is a group of $m$ proposed talks with preset starting and end times. Suppose that talk $t_j$ begins at time $s_j$ and ends at time $e_j$.

Without loss of generality, we assume that the talks are listed in order of nondecreasing ending time, so that $e_{1} \leq e_{2} \leq \cdots \leq e_{m}$. The greedy algorithm proceeds by selecting at each stage a talk with the earliest ending time among all those talks that begin no sooner than when the last talk scheduled in the main lecture hall has ended. Note that a talk with the earliest end time is always selected first by the algorithm.We will show that this greedy algorithm is optimal in the sense that it always schedules the most talks possible in the main lecture hall. To prove the optimality of this algorithm we use mathematical induction on the variable $n$, the number of talks scheduled by the algorithm. We let $P(n)$ be the proposition that if the greedy algorithm schedules $n$ talks in the main lecture hall, then it is not possible to schedule more than $n$ talks in this hall. 

**Base Step:** Suppose the greedy algorithm managed to schedule just one talk, $t_1$, in the lecture hall. This means that no other talk can start at or after $e_1$, the end time of $t_1$. Otherwise, the first such talk we come to as we go through the talks in order of nondecreasing end times could be added. Hence, at time $e_1$ each of the remaining talks start before $e_1$ and end after $e_1$. It follows that no two talks can be scheduled because both need to use the same lecture hall at time $e_1$. This shows that $P(1)$ is true and completes the basis step. 

**Inductive Step:** 
The inductive hypothesis is that $P(k)$ is true, where $k$ is an arbitrary positive
integer, that is, that the greedy algorithm always schedules the most possible talks when it selects
$k$ talks, where $k$ is a positive integer, given any set of talks, no matter how many.We must show
that $P(k + 1)$ follows from the assumption that $P(k)$ is true, that is, we must show that under
the assumption of $P(k)$, the greedy algorithm always schedules the most possible talks when it
selects $k + 1$ talks.
Now suppose that the greedy algorithm has selected $k + 1$ talks. Our first step in completing
the inductive step is to show there is a schedule including the most talks possible that contains
talk $t_1$, a talk with the earliest end time. This is easy to see because a schedule that begins
with the talk $t_i$ in the list, where $i \gt 1$, can be changed so that talk $t_1$ replaces talk $t_i$. To see
this, note that because $e_1 \le e_i$, all talks that were scheduled to follow talk $t_i$ can still be scheduled.
Once we included talk $t_1$, scheduling the talks so that as many as possible are scheduled
is reduced to scheduling as many talks as possible that begin at or after time $e_1$. So, if we
have scheduled as many talks as possible, the schedule of talks other than talk $t_1$ is an optimal schedule of the original talks that begin once talk $t_1$ has ended. Because the greedy algorithm
schedules $k$ talks when it creates this schedule, we can apply the inductive hypothesis to conclude
that it has scheduled the most possible talks. It follows that the greedy algorithm has scheduled
the most possible talks, $k + 1$, when it produced a schedule with $k + 1$ talks, so $P(k + 1)$ is
true. This completes the inductive step.
We have completed the basis step and the inductive step. So, by mathematical induction we
know that $P(n)$ is true for all positive integers $n$. This completes the proof of optimality. That is,
we have proved that when the greedy algorithm schedules $n$ talks, when $n$ is a positive integer,
then it is not possible to schedule more than $n$ talks. $\blacksquare$




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
In a proof by strong induction, the inductive step shows that if $P(j)$ is true for all positive integers $j$ not exceeding $k$, then $P(k+1)$ is true. That is, for the inductive hypothesis we assume that $P(j)$ is true for $j=1,2, \ldots, k$.

In other words, to prove $P(n)$ is true for all positive integers $n$, where $P(n)$ is a propositional function, we complete two steps:

1) **Basis Step**: We verify that the proposition $P(1)$ is true.

2) **Inductive Step:** We show that the conditional statement $[P(1) \wedge P(2) \wedge \cdots \wedge P(k)] \rightarrow P(k+1)$ is true for all positive integers $k$.

## Examples

### Products of Primes
**Lemma 1:** Every integer greater than $1$ is a product of primes.
**Proof:** Our induction hypothesis 
$$P(n)=n+2 \medspace\text {is the product of primes}$$
So our lemma will follow if we prove that $P(n)$ holds for all $n \ge 0$.

**Base Case:** $P(0)$ is true because $0 + 2$ is prime, and so is a product of primes by convention.

**Inductive Step:** Suppose that $n \ge 0$ and that $i+2$ is a product of primes for every natrual number $1 \lt n+1$. We must show that $P(n+1)$ holds, namely, that $n+3$ is also a product of primes. We argue by cases:

If $n+3$ is itself prime, then it is a product of primes by convention, so $P(n+1)$ holds in this case. 

Otherwise, $n+3$ is not prime, which means that $n+3=km$ for some natural numbers $k, m$ such that $2 \leq k, m<n+3$. So $k-2$ is a natural number less than $n+1$, which means that $(k-2) + 2$ is a product of primes by induction hypothesis. That is, $k$ is a product of primes. Likewise, $m$ is a product of primes. So $km=n+3$ is also a prioduct of primes. Therefore $P(n+1)$ holds in this case as well.

So $P(n+1)$ holds in any case, which completes the proof by strong induction that $P(n)$ holds for all natural numbers $n$. $\blacksquare$
