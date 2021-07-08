---
title: Program Correctness
description: 
published: true
date: 2021-07-08T18:56:17.254Z
tags: computer-science, discrete-mathematics, algorithms
editor: markdown
---

# Program Verification
A proof that a program is **correct** (always produces the correct output for every possible input) consists of two parts:
1) Show that the correct answer is obtained if the program terminates. This part of the proof establishes the **partial correctness** of the program. 
2) Show that the program always terminates. 

## Specifying Correct Program Output
Two propositions are used to specify a program produces the correct output:
1) **Initial Assertion** - Gives properties that the input values must have.
2) **Final Assertion** - Gives the properties that the output of the program should have, if the program did what was intended. 

The appropriate and final assertions must be provided when a program is checked.

A program, or program segment, $S$ is said to be **partially correct with respect to** the initial assertion $p$ and the final assertion $q$ if whenever $p$ is true for the input values of $S$ and $S$ terminates, then $q$ is true for the output values of $S$. The notation $p\{S\} q$ indicates that the program, or program segment, $S$ is partially correct with respect to the initial assertion $p$ and the final assertion $q$.

## Rules of Inference

### Composition Rule
The **composition rule**, which can be stated as 
$$
\begin{aligned}
& p\left\{S_{1}\right\} q \\
& q\left\{S_{2}\right\} r \\
\hline \therefore \medspace
& p\left\{S_{1} ; S_{2}\right\} r
\end{aligned}
$$

It is stating that a program $S$ is split into subprograms $S_1$ and $S_2$. $S=S_1;S_2$ indicates $S$ is made up of $S_1$ followed by $S_2$. 

Suppose that the correctness of $S_{1}$ with respect to the initial assertion $p$ and final assertion $q$, and the correctness of $S_{2}$ with respect to the initial assertion $q$ and the final assertion $r$, have been established. It follows that if $p$ is true and $S_{1}$ is executed and terminates, then $q$ is true; and if $q$ is true, and $S_{2}$ executes and terminates, then $r$ is true. 

Thus, if $p$ is true and $S=S_{1} ; S_{2}$ is executed and terminates, then $r$ is true. 

### If Statement Rule of Inference
$$
\begin{aligned}
& (p \wedge \text { condition })\{S\} q \\
& (p \wedge \neg \text { condition }) \rightarrow q\\
\hline \therefore \medspace
& p\{\text { if condition then } S\} q
\end{aligned}
$$
For the program segment
```
if condition then 
    S
```
where $S$ is a block of statements. Then $S$ is executed iff condition is true.

To verify this particular program segment is correct with respect to the initial assertion $p$ and final assertion $q$, two things must be shown:
1) When $p$ is true and **condition** is also true, then $q$ is true after $S$ terminates.
2) When $p$ is true and **condition** is false, then $q$ is true (because $S$ does not execute).

### If Else Statement Rule of Inference
$$
\begin{aligned}
& (p \wedge \text { condition })\{S_1\} q \\
& (p \wedge \neg \text { condition })\{S_2\}q\\
\hline \therefore \medspace
& p\{\text { if condition then } S_1 \medspace \text {else} \medspace S_2 \} q
\end{aligned}
$$
<pre>
if condition then 
	S<sub>1</sub>
else 
	S<sub>2</sub>
</pre>
To verify this particular program segment is correct with respect to the initial assertion $p$ and final assertion $q$, two things must be shown:
1) When $p$ is true and **condition** is true, then $q$ is true after $S_1$ terminates.
2) When $p$ is true and **condition** is false, then $q$ is true after $S_2$ terminates.
