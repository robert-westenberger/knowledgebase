---
title: Set Operations
description: 
published: true
date: 2021-04-12T03:35:41.680Z
tags: discrete-mathematics
editor: markdown
---

# Rosen Discrete Mathematics 7th Edition Section 2.2

## Proving Set Identities
### 5
Prove the complementation law by showing $\overline{\overline{\huge A}}=A$
(assume that $A$ is a subset of some underlying
universal set $U$)
#### Solution
$\overline{\overline{\huge A}}$ is the complement of $\overline{\huge A}$. That is, $\overline{\overline{\huge A}} = \{x \in U \mid x \notin \overline{\huge A}\}$. $x \notin \overline{\huge A}$ means $x \in A$. Represented differently, $\overline{\overline{\huge A}}=\{x \mid \neg x \in \overline{\huge A}\}=\{x \mid \neg \neg x \in A\}=\{x \mid x \in A\}=A$.

### 7
Prove the domination laws by showing 
**a)** $A \cup U=U$
**b)** $A \cap \emptyset=\emptyset$
(assume that $A$ is a subset of some underlying
universal set $U$)
#### Solution
**a)** $A \cup U=\{x \mid x \in A \vee x \in U\} =\{x \mid x \in A \vee \mathbf{T}\}=\{x \mid \mathbf{T}\}=U$.
**b)** $A \cap \emptyset=\{x \mid x \in A \wedge x \in \emptyset\}=\{x \mid x \in A \wedge \mathbf{F}\}=\{x \mid \mathbf{F}\}=\emptyset$

### 9 
Prove the complement laws by showing that 
**a)** $A \cup \bar{A}=U$
**b)** $A \cap \bar{A}=\emptyset$

(assume that $A$ is a subset of some underlying
universal set $U$)

#### Solution
**a)** $A \cup \bar{A}= \{ x \mid x \in A \vee x \in \bar A\} = \{ x \mid x \in A \vee x \in \bar A\} =U$