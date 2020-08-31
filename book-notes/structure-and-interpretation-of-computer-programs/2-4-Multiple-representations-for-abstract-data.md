---
title: Section 2.4 Multiple Representations for Abstract Data
description: 
published: true
date: 2020-08-31T01:54:40.049Z
tags: book-notes
editor: markdown
---

# Multiple Representations for Abstract Data
Using data abstraction, we can isolate two different representations for complex numbers. No matter which representation is chosen (between rectangular form ( real part / imaginary part ) and polar form (magnitude and angle), any operation which the program has available can be performed on the complex numbers stored in the program. 

The program contains selectors and constructors for representing and retrieving complex numbers as rectangular form and polar form. The program contains functions that return the polar form or parts of it if given the rectangular form and vice versa. 

Data abstraction can be viewed as the application of the **principle of least commitment**. The choice of a concrete representation for the complex numbers can be deferred until the last possible moment, retaining maximum flexibilty in the system design. 

Both representations can be used in the same system. The only thing that is needed is a way to distinguish data in polar form from data in rectangular form.Otherwise, if we were asked, for instance, to find the magnitude of the pair (3,4), we wouldn't know whether to answer 5 (interpreting the number in rectangular form) or 3 (interpreting the number in polar form). This can be accomplished with tagged data. Data objects for complex numbers that are in either rectangular form or polar form can be identified and then manipulated based off of what type they are.

![complex_numbers_program.png](/complex_numbers_program.png)

Above program uses data tags to tag the different representations. When the different representations are processed, data tags are added or stripped when they are interfacing with higher or lower level parts of the system. 




