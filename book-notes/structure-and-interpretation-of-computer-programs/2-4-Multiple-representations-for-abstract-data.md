---
title: Section 2.4 Multiple Representations for Abstract Data
description: 
published: true
date: 2020-08-31T00:16:30.742Z
tags: book-notes
editor: markdown
---

# Multiple Representations for Abstract Data
Using data abstraction, we can isolate two different representations for complex numbers. No matter which representation is chosen (between rectangular form ( real part / imaginary part ) and polar form (magnitude and angle), any operation which the program has available can be performed on the complex numbers stored in the program. 

The program contains selectors and constructors for representing and retrieving complex numbers as rectangular form and polar form. The program contains functions that return the polar form or parts of it if given the rectangular form and vice versa. 

Data abstraction can be viewed as the application of the **principle of least commitment**. The choice of a concrete representation for the complex numbers can be deferred until the last possible moment, retaining maximum flexibilty in the system design. 