---
title: Section 3.1 Assignment and Local State
description: 
published: true
date: 2020-12-20T06:01:16.364Z
tags: book-notes
editor: markdown
---

# Assignment and Local State
Programming that makes extensive use of assignment is known as imperative programming.

Programming without the use of assignments is known as functional programming and is deterministic ( there are no side effects. Given inputs will always produce the same outputs ). 

Assignment can improve the modularity of systems. It allows us to model objects that have local state. 

Introducing assignment however breaks the substitution model of function application. The substitution model cannot account for changing internal state from call to call.

The substitution model is based on the notion that symbols are essentially names for values. This doesn't work with variables because its value can change with assignment so it can't simply be a name for a value (that value changes). 

Progams with assignment are susceptible to bugs that cannot occur in function programs. If we write assignments in the wrong order in imperative programming that may produce an incorrect result. This problem straight up doesn't exist in functional programming.

 
