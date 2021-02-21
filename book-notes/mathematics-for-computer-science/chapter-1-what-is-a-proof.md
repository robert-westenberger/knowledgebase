---
title: Chapter 1: What is a Proof?
description: 
published: true
date: 2021-02-21T05:54:20.471Z
tags: computer-science, mathematics, book-notes, discrete-mathematics
editor: markdown
---

# What is a Proof? 

## Propositions
A **mathematical proof** of a **proposition** is a chain of **logical deductions** leading to the proposition from a base set of **axioms**. 

A **proposition** is a statement that is either true or false. 

**Claim:** For every nonnegative integer n the value of $n^2+n+41$ is prime.
$$p(n) ::=n^2 + n + 41$$

We can check $n=0$ to $n=39$ and the claim holds true. However, for $n=40$ we get $40^2 + 40 + 41 = 41* 41$ which is not prime. This example highlights, in general, you can't check a claim about an infinite set by checking a finite sample of its elements, no matter how large the sample. 

There is a special notation for propositions about all numbers or all items of a certain kind: 

$$\forall n \in \natnums .p(n) \medspace \text{is prime.}$$

It reads: "For all n in the set of nonnegative integers, p(n) is prime.

## Predicates
A **predicate** can be understood as a proposition whose truth depeonds on the value of one or more variables. "n is a perfect square" is a predicate, since you don't know its true or false until a value for n is provided.

## The Axiomatic Method

**Axioms** are statements or propositions taken to be true. Using these axioms, proofs can be developed. A **proof** is a sequence of logical deductions from axioms and previously proved statements that conludes with the proposition in question. 

* Important true propositons are called theorems. 
* A lemma is a preliminary proposition useful for proving later propositions. 
* A crollary is a proposition that folows in just a few logical steps from a theorem.

## Our Axioms

### Logical Deductions
Logical deductions, or inference rules, are used to proce new propositions by using previously proved ones. 

$$
\frac{P, \quad P \text { IMPLIES } Q}{Q}
$$
A proof of $P$ together with a proof $P \medspace \text{IMPLIES} \medspace Q$ is a proof of $Q$.

When the statements are above the line, called the **antecedents**, are proved, we can consider the statement below the line, the **conclusion** or **consequent**, to be true.

$$
\frac{P \text { IMPLIES } Q, \quad Q \text { IMPLIES } R}{P \text { IMPLIES } R}
$$
$$
\frac{\text { NOT }(P) \text { IMPLIES } \operatorname{NOT}(Q)}{Q \text { IMPLIES } P}
$$

Each step in a proof should be clear and "logical"; in particular, one should state what previously proved facts are used to derive each new conclusion.

### Patterns of Proof

A proof can be any sequence of logical deductions. Many proofs follow one of a handful of standard templates. Each proof has it own details, of course, but these templates at least provide you with an outline to fill in.

## Proving an Implication
Propositions of the form "If $P$, then $Q$" are called implications. 

Its often rephrased as $P \text { IMPLIES } Q$

* Quadratic Formula - If $ax^2 + bx + c = 0 \medspace \text{and} \medspace a \not = \text{, then} \medspace x=\left(-b \pm \sqrt{b^{2}-4 a c}\right) / 2 a$.

### Method #1 
In order to prove $P \text { IMPLIES } Q$: 
1) Write, "Assume P".
2) Show that Q logically follows. 

#### Example of Method #1

**Theorem:** $\text { If } 0 \leq x \leq 2 \text { , then }-x^{3}+4 x+1>0$

**Scratchwork:** We can factor $-x^3 + 4x$ to get $-x^3 + 4x = x(2-x)(2+x)$ .For $x$ between 0 and 2, all the terms on the right side are nonnegative. We can organize our observations into a formal proof.

**Proof:** Assume $0 \leq x \leq 2$. Then, $x$, $2-x$, and $2+x$ are all nonnegative. Therefore, the product of these terms is also nonnegative. Adding 1 to this product gives a positive number, so:
$$x(2-x)(2+x)+1>0$$
Multiplying out on the left side proves that 
$$
-x^{3}+4 x+1>0
$$ 
as claimed. $\blacksquare$

Note: Proofs typically begin with the word "Proof" and end with some sort of delimiter like $\square$, $\blacksquare$, or "QED".

### Method #2 - Prove the Contrapositive
An implication $P \text { IMPLIES } Q$ is logically equivalent to its contrapositive $\operatorname{NOT}(Q)$ IMPLIES $\operatorname{NOT}(P)$.

1) Write, "We prove the contrapositive:" and then tstate the contrapositive.
2) Proceed as in Method #1. 

#### Example of Method #2
**Theorem:** $\text{If r is irrational, then} \medspace \sqrt r \medspace \text{is also irrational}$.
**Scratchwork:** A number is irrational when there is no quotient of integers to which it is equal. We must show that if r is not a ratio of integers, then $\sqrt r$ is also not a ratio of integers. We can eliminate both not's and simplify the proof by using the contrapositive instead.
**Proof:** We prove the contrapositive: if $\sqrt r$ is rational, then $r$ is rational. Assume that $\sqrt r$ is rational. Then there exists integers $m$ and $n$ such that:
$$\sqrt r = \frac m n$$
Squaring both sides gives: 
$$r = \frac{m^2}{n^2}$$
Since $m^2$ and $n^2$ are integers, r is also rational. $\blacksquare$

## Proving an "If and Only If"
Many theorems assert that two statements are logically equivalent; that is one holds if and only if (iff) the other does. 

Example: Two triangles have the same side lengths if and only if two side lengths and the angle between those sides are the same.

### Method #1: Prove Each Statement Implies the Other
The statement $P \text { IFF } Q$ is equivalent to the two statements $P \text { IMPLIES } Q$ and $Q \text { IMPLIES } P$. You can prove "iff" by proving two implications.
1) Write, "We prove P imoplies Q and vice-versa"
2) Write, “First, we show P implies Q.” . 
3) Write, “Now, we show Q implies P.”

### Method #2: Construct a Chain of Iffs
1. Write, “We construct a chain of if-and-only-if implications.” 
2. Prove P is equivalent to a second statement which is equivalent to a third statement and so forth until you reach $Q$.


#### Example of Method #2
The standard deviation of a sequence of values $x_{1}, x_{2}, \ldots, x_{n}$ is defined to be:
$$
\sqrt{\frac{\left(x_{1}-\mu\right)^{2}+\left(x_{2}-\mu\right)^{2}+\cdots+\left(x_{n}-\mu\right)^{2}}{n}}
$$
where $\mu$ is the average/mean of the values.
$$
\mu::=\frac{x_{1}+x_{2}+\cdots+x_{n}}{n}
$$
**Theorem:** The standard deviation of a sequence of values $x_{1}, x_{2}, \ldots, x_{n}$ is zero iff all the values are equal to the mean.

For example, the standard deviation of class scores is 0 iff everyone scored exactly the class average.

**Proof:** We construct a chain of "iff" implications, starting with the statement that the standard deviation is zero.
$$
\sqrt{\frac{\left(x_{1}-\mu\right)^{2}+\left(x_{2}-\mu\right)^{2}+\cdots+\left(x_{n}-\mu\right)^{2}}{n}}=0
$$

Now since zero is the only number whose root is 0, the above equation holds iff 
$$
\left(x_{1}-\mu\right)^{2}+\left(x_{2}-\mu\right)^{2}+\cdots+\left(x_{n}-\mu\right)^{2}=0
$$
Squares of real numbers are always nonnegative, so every term on the left hand side is nonnegative. This means that the above equation holds iff 
*Every term on the left-hand side is zero.*
But a term $\left(x_{i}-\mu\right)^{2}$ is zero iff $x_{i}=\mu$, so the preceding statement is true iff every $x_i$ equals the mean. $\blacksquare$

## Proof by Cases
Otherwise known as proof by exhaustion. 

**Theorem:** If an integer is a perfect cube, then it must be either a multiple of 9, 1 more than a multiple of 9, or 1 less than a multiple of 9.

**Proof:** The proof is by case analysis. Each perfect cube is the cube of some integer n, where n is either a multiple of 3, 1 more than a multiple of 3, or 1 less than a multiple of 3. So these three cases are exhaustive:
*  Case 1: If $n=3p$, then $n^3 = 27p^3$, which is a multipole of 9.
* Case 2: If $n = 3p + 1$, then $n^3 = 27p^3 + 27p^2 + 9p + 1$, which is 1 more than a multiple of 9. For instance, if $n = 4$ then $n^3 = 64 = 9×7 + 1$.
* Case 3: If $n = 3p − 1$, then $n3 = 27p^3 − 27p^2 + 9p − 1$, which is 1 less than a multiple of 9. For instance, if $n = 5$ then $n3 = 125 = 9×14 − 1$. 
$\blacksquare$

## Proof by Contradiction
Otherwise known as an **indirect proof**, you show that if a proposition were false, then some false fact would be true. Since a false fact by definition can't be true, then the proposition must be true.

### Method
1. Write "We use proof by contradiction."
2. Write, "Suppose P is false."
3. Deduce something known to be false (a logical contradiction). 
4. Write, "This is a contradiction. Therefore, P must be true."


#### Example 
**Theorem:** $\sqrt 2$ is irrational.

**Proof:** We use proof by contradiciton. Suppose that the claim is false and 
$\sqrt 2$ is rational. We can write $\sqrt 2$ as a fraction $n/d$ in lowest terms.

Squaring both sides gives us $2 = n^2/d^2$ so 2d^2 = n^2. This implies that n is a multiple of 2. Therefore $n^2$ must be a multiple of 4. But since $2d^2 = n^2$, we know $2d^2$ is a multiple of 4 and so $d^2$ is a multiple of 2. That implies d is a multiple of 2.

So, the numerator and the denominator have 2 as a common factor, which contradicts that fact that $n/d$ is in lowest terms. Thus, $\sqrt 2$ must be irrational. $\blacksquare$

## Good Proofs in Practice
A good proof must be clear and correct. A good proof may differ between audiences (e.g. professional mathematicians vs those just beginning studying proofs).

* **State your game plan.** A good proof begins by explaining the general line of reasoning, for example, “We use case analysis” or “We argue by contradiction.”

* **Keep a linear flow.** Sometimes proofs are written like mathematical mosaics, with juicy tidbits of independent reasoning sprinkled throughout. This is not good. The steps of an argument should follow one another in an intelligible order.

* **A proof is an essay, not a calculation.** Many students initially write proofs the way they compute integrals. The result is a long sequence of expressions without explanation, making it very hard to follow. This is bad. A good proof usually looks like an essay with some equations thrown in. Use complete sentences.

* **Avoid excessive symbolism.** Your reader is probably good at understanding words, but much less skilled at reading arcane mathematical symbols. Use words where you reasonably can.

* **Revise and simplify.** Your readers will be grateful.

* **Introduce notation thoughtfully.** Sometimes an argument can be greatly simplified by introducing a variable, devising a special notation, or defining a new term. But do this sparingly, since you’re requiring the reader to remember all that new stuff. And remember to actually define the meanings of new variables, terms, or notations; don’t just start using them!

* **Structure long proofs.** Long programs are usually broken into a hierarchy of smaller procedures. Long proofs are much the same. When your proof needed facts that are easily stated, but not readily proved, those fact are best pulled out as preliminary lemmas. Also, if you are repeating essentially the same argument over and over, try to capture that argument in a general lemma, which you can cite repeatedly instead.
* **Be wary of the “obvious.”** When familiar or truly obvious facts are needed in a proof, it’s OK to label them as such and to not prove them. But remember that what’s obvious to you may not be—and typically is not—obvious to your reader. 

	Most especially, don’t use phrases like “clearly” or “obviously” in an attempt to bully the reader into accepting something you’re having trouble proving. Also, go on the alert whenever you see one of these phrases in someone else’s proof.

* **Finish.** At some point in a proof, you’ll have established all the essential facts you need. Resist the temptation to quit and leave the reader to draw the “obvious” conclusion. Instead, tie everything together yourself and explain why the original claim follows.
