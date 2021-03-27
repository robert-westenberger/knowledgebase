---
title: Propositional Logic
description: 
published: true
date: 2021-03-27T03:08:23.822Z
tags: computer-science, mathematics, discrete-mathematics
editor: markdown
---

# Propositional Logic

## Propositions
A statement that is either true or false. 

A proposition is **atomic** if it cannot be broken down into smaller statements / propositions. Otherwise, it is called **molecular**. 


## Logical Connectives
$$
\begin{array}{cc}
\text { Symbol } & \text { Meaning } \\
\hline \vee & \text { or } \\
\wedge & \text { and } \\
\rarr & \text { implication (or conditional) } \\
\leftrightarrow & \text { biconditional } \\
\neg & \text { not }
\end{array}
$$

$P \vee Q$ is read "P or Q"
$P \wedge Q$ is read "P and Q"
$P \rarr Q$ is read "if P then Q"
$P \leftrightarrow Q$ is read "P if and only if Q"
$\neg P$ is read "not P"

Note that the OR is the **inclusive or** and that $P \vee Q$ is true when both P and Q are true.
## Truth Conditions for Connectives

$P \vee Q$ is true when P or Q or both are true
$P \wedge Q$ is true when both P and Q are true
$P \rarr Q$ is true when P is false or Q is true or both
$P \leftrightarrow Q$ is true when P and Q are both true, or both false.
$\neg P$ is true when P is false.

## Negation
Note that the notation for negation isn't standardized. $\neg p$ and $\bar{p}$ are the most common, you might also see $\sim p$, $-p$, $p^{\prime}$, $Np$, and $!p$

The negation of the English sentence "Bob’s smartphone has at least 32 GB of memory” is “Bob’s smartphone does not have at least 32 GB of memory”. This could be rewritten more simply as "Bob's cellphone has less than 32 GB of memory."

Note how in this specific case, "greater than or equal to 32 GB" becomes "less than 32GB" so we go from $\ge$ to $\lt$


## Implications
$P \rarr Q$  "if P then Q". Often rephrased as $P \text { IMPLIES } Q$.

P is the **hypothesis** (or **antecedent**)
Q is the **conclusion** (or **consequent**)

An implication is true provided P is false or Q is true (or both), and false otherwise. In particular, the only way for P → Q to be false is for P to be true and Q to be false.

* Quadratic Formula - If $ax^2 + bx + c = 0 \medspace \text{and} \medspace a \not = \text{, then} \medspace x=\left(-b \pm \sqrt{b^{2}-4 a c}\right) / 2 a$.

### Converse Inverse, and Contrapositive
The **converse** of an implication $P \rarr Q$ is the implication $Q \rarr P$. An example of a true implication and a false converse woul be, "If a shape is a square, then it is a rectangle". Or, "If a number greater than 2 is prime, then that number is odd" (Just because a number is odd does not mean it is prime). 

There can be implications that's converse is also true. For example, the pythagorean theorem has a true converse. Is $a^2 + b^2 = c^2$, then the triangle with sides a, b, and c is a right triangle.


The **contrapositive** of an implication $P \rarr Q$ is the statement $\neg Q \rarr \neg P$. An implication and its contrapositive are logically equivalent. The contrapositive can be helpful in deciding whether an implication is true: often it is easier to analyze the contrapositive.

If an implication and its converse are true, we say that P and Q are equivalent and write $P \leftrightarrow Q$ ( the biconditional).

The **inverse** of a proposition $P \rarr Q$ is $\neg P \rarr \neg Q$
### If and only if
$P \leftrightarrow Q$ is logically equivalent to $(P \rarr Q) \wedge (Q \rarr P)$.

Example: Given an integer $n$, it is true that $n$ is even if and only if $n^2$ is even. That is, if $n$ is even, then $n^2$ is even, as well as the converse: if $n^2$ is even, then $n$ is even.

#### Proof Method #1 
In order to prove $P \text { IMPLIES } Q$: 
1) Write, "Assume P".
2) Show that Q logically follows. 

##### Example 1 of Proof Method #1

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
##### Example 2 of Method #1
**Theorem:** If two numbers $a$ and $b$ are even, then their sum $a + b$ is even.
**Proof:** Assume the numbers $a$ and $b$ are even. This means that $a = 2k$ and $b=2j$ for some integers $j$ and $k$. The sum is then $a+b=2k+2j=2(k+j)$. Since $k+j$ is an integer, this means that $a+b$ is even. $\blacksquare$

Notice we just assume P is true and repeatedly ask and answer the question, "What does that mean?". Eventually we conclude that it means the conclusion.

### Logic and Bit Operations
Computer **bit operations** correspond to the logical connectives. 
Below is a table for the bit operators OR ($\vee$)
$$
\begin{array}{c|c|c|c|c}
 &  & OR & AND & XOR \\
\boldsymbol{x} & \boldsymbol{y} & \boldsymbol{x} \vee \boldsymbol{y} & \boldsymbol{x} \wedge \boldsymbol{y} & \boldsymbol{x} \oplus \boldsymbol{y} \\
\hline 0 & 0 & 0 & 0 & 0 \\
0 & 1 & 1 & 0 & 1 \\
1 & 0 & 1 & 0 & 1 \\
1 & 1 & 1 & 1 & 0
\end{array}
$$
# Applications of Propositional
Propositional logic and its rules can be used to design computer circuits, to construct computer programs, to verify the correctness of those programs, and to solve many familiar puzzles. Software systems based on the rules of logic have been developed for constructing some, but not all, types of proofs automatically

## Translating English Sentences
“You cannot ride the roller coaster if you are under 4 feet tall unless you are older than 16 years old., where 

$q$ "You can ride the roller coaster"
$r$ "You are under 4 feet tall"
$s$ "You are older than 16 years old"

$$
(r \wedge \neg s) \rightarrow \neg q
$$
(There are other ways to represent this sentence)
## Boolean Searches
## Logic Puzzles
## Logic Circuits

# Propositional Equivalences
A compound proposition that is always true, no matter the truth values of the propositional variables that occur in it, is a **tautology**. A compound proposition that is always false is a **contradiction**.

## De Morgans Laws
$$
\begin{array}{l}
\neg(p \wedge q) \equiv \neg p \vee \neg q \\
\neg(p \vee q) \equiv \neg p \wedge \neg q
\end{array}
$$

De Morgan's laws for negating conjunctions and disjunctions.
## Conditional-Disjunction Equivalence
$p \rarr q$ and $\neg p \vee q$ are logically equivalent.
$$
\begin{array}{cc|c|c|c}
\boldsymbol{p} & \boldsymbol{q} & \neg \boldsymbol{p} & \neg \boldsymbol{p} \vee \boldsymbol{q} & \boldsymbol{p} \rightarrow \boldsymbol{q} \\
\hline \mathrm{T} & \mathrm{T} & \mathrm{F} & \mathrm{T} & \mathrm{T} \\
\mathrm{T} & \mathrm{F} & \mathrm{F} & \mathrm{F} & \mathrm{F} \\
\mathrm{F} & \mathrm{T} & \mathrm{T} & \mathrm{T} & \mathrm{T} \\
\mathrm{F} & \mathrm{F} & \mathrm{T} & \mathrm{T} & \mathrm{T}
\end{array}
$$

## Constructing New Logical Equivalences
Below, we show that $\neg(p \rightarrow q)$ and $p \wedge \neg q$ are logically equivalent. 
$$
\begin{aligned}
\neg(p \rightarrow q) & \equiv \neg(\neg p \vee q) & \text {conditional-disjunction equivalence} \\
& \equiv \neg(\neg p) \wedge \neg q & \text {De Morgan law} \\
& \equiv p \wedge \neg q & \text {double negation law}
\end{aligned}
$$

Another example, we show that $\neg(p \vee(\neg p \wedge q))$ and $\neg p \wedge \neg q$ are logically equivalent by developing a series of logical equivalences.
$$
\begin{aligned}
\neg(p \vee(\neg p \wedge q)) & \equiv \neg p \wedge \neg(\neg p \wedge q) & \text {second De Morgan law} \\
& \equiv \neg p \wedge[\neg(\neg p) \vee \neg q] & \text {first De Morgan law} \\
& \equiv \neg p \wedge(p \vee \neg q) & \text {double negation law} \\
& \equiv (\neg p \wedge p) \vee(\neg p \wedge \neg q) & \text {second distributive law} \\
& \equiv \mathbf{F} \vee(\neg p \wedge \neg q) & \text {because} \neg p \wedge p \equiv \mathbf{F} \\
& \equiv (\neg p \wedge \neg q) \vee \mathbf{F} & \text {by the commutative law for disjunction} \\
& \equiv \neg p \wedge \neg q & \text {by the identity law for } \mathbf{F} \\
\end{aligned}
$$
## Satisfiability
A compound proposition is **satisfiable** if there exists an assignment of truth values to its variables that makes it true (when its a tautology or contingency). 

When a compound proposition is false for all assignments of truth values to its variables, it is **unsatisfiable**.


$(p \vee \neg q) \wedge(q \vee \neg r) \wedge(r \vee \neg p) \wedge(p \vee q \vee r) \wedge(\neg p \vee \neg q \vee \neg r)$ is an example of unsatisfiable. For it to be true, both $(p \vee \neg q) \wedge(q \vee \neg r) \wedge(r \vee \neg p)$ and $(p \vee q \vee r) \wedge(\neg p \vee \neg q \vee \neg r)$ must both be true. But for the former, all three variables must have the same truth variable and for the latter at least one must be true and one must be false. This is a contradiction, so we can conclude that there does not exist an assignment of truth variables that makes the compound proposition true.

### Applications of Satisfiability
Many problems in diverse areas such as robotics, software testing, artificial intelligence planning, computer-aided design, machine vision, integrated circuit design, scheduling, computer networking, and genetics, can be modeled in terms of propositional satisfiability. 

### Examples of Applications of Satisfiability

#### n Queens Problem 

The $n$ queens problem asks for a placement of $n$ queens on an $n \times n$ chessboard so that no queen can attack another queen. This means that no two queens can be placed in the same row, column, or diagonal to one another.


![n_queens.png](/n_queens.png)
($i$th row $j$th column, starting from top left square)

To model this as a satisfiability problem, we introduce $n^2$ variables $p(i, j)$ for $i=1,2, \ldots, n$  and $j=1,2, \ldots, n$. For a given placement of a queens on the chessboard, $P(i, j)$ is true when there is a queen on the square in the $ith$ row and $jth$ column, and is false otherwise. 

Note that squares $(i, j)$ and $\left(i^{\prime}, j^{\prime}\right)$ are on the same diagonal if either $i+i^{\prime}=j+j^{\prime}$ or $i-i^{\prime}=j-j^{\prime}$. Note in the picture above of our chessboard, $p(6, 2)$ and $p(2,1)$ are true, and $p(3, 4)$ and $p(5, 4)$ are false. 

For no two of the $n$ queens to be in the same row, there must be one queen in each row. We can show that there is one queen in each row by verifying that every row contains at least one queen and that every row contains at most one queen.

We note that $\bigvee_{j=1}^{n} p(i, j)$ asserts that row $i$ contains at least one queen, and 
$$
Q_{1}=\bigwedge_{i=1}^{n} \bigvee_{j=1}^{n} p(i, j)
$$
asserts that every row contains at least one queen. 

For every row to include at most one queen, it must be the case that $p(i, j)$ and $p(k, j)$ are not both true for integers $j$ and $k$ with $1 \leq j<k \leq n$. Observe that $\neg p(i, j) \vee \neg p(i, k)$ asserts that at least one of $\neg p(i, j)$ and $\neg p(i, k)$ is true, which means that at least one of $p(i, j)$ and $p(i, k)$ is false. So to check that there is at most one queen in each row, we assert 

$$
Q_{2}=\bigwedge_{i=1}^{n} \bigwedge_{j=1}^{n-1} \bigwedge_{k=j+1}^{n}(\neg p(i, j) \vee \neg p(k, j))
$$

To assert that no column contains more than one queen, we assert that 

$$
Q_{3}=\bigwedge_{j=1}^{n} \bigwedge_{i=1}^{n-1} \bigwedge_{k=i+1}^{n}(\neg p(i, j) \vee \neg p(k, j))
$$
(This assertion, together with the previous assertion that every row contains a queen, implies that every column contains a queen.)

To assert that no diagonal contains two queens, we assert
$$
Q_{4}=\bigwedge_{i=2}^{n} \bigwedge_{j=1}^{n-1} \bigwedge_{k=1}^{\min (i-1, n-j)}(\neg p(i, j) \vee \neg p(i-k, k+j))
$$

and 

$$
Q_{5}=\bigwedge_{i=1}^{n-1} \bigwedge_{j=1}^{n-1} \bigwedge_{k=1}^{\min (n-i, n-j)}(\neg p(i, j) \vee \neg p(i+k, j+k))
$$

The innermost conjunction in $Q_4$ and in $Q_5$ for a pair $(i, j)$ runs through the positions on a diagonal that begin at $(i, j)$ and runs rightward along this diagonal. The upper limits on these innermost conjunctions identify the last cell in the board on each diagonal. 

Putting this all together, the solution to the $n$ queens problem are the assignments of truth values to the variables $p(i, j)$ for $i=1,2, \ldots, n$  and $j=1,2, \ldots, n$ that make 

$$
Q=Q_{1} \wedge Q_{2} \wedge Q_{3} \wedge Q_{4} \wedge Q_{5}
$$

true.  

So to recap: 
$Q_1$ is a conjunction of disjunctions which require for every row there is at least one queen.

The rest of the constraints are forbidding pairs of queens from being placed at certain locations. 
$Q_2$ is forbidding placing two queens in the same row. That is, we for forbid $p(i, j) \wedge p(i, k)$

