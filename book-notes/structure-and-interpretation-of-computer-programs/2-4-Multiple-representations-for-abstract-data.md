---
title: Section 2.4 Multiple Representations for Abstract Data
description: 
published: true
date: 2020-11-17T18:17:01.307Z
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

**Data-directed programming** can be used to modularize the system even further. Whenever we deal with a set of generic operations that are common to a set of different types we are, in effect, dealing with a two dimensional table that contains the possible operations on one axis and the possible types on the other axis. The entries in the table are the functions that implement each operation for each type of argument presented. 

![complex_number_operation_table.png](/complex_number_operation_table.png)
The current operations table for the complex number program.
Following helper functions..
`put(op, type, item)`
installs the item in the table, indexed by the op and the type.
`get(op, type)`
looks up the op, type entry in the table and returns the item found there. If no item is found, get returns a unique primitive value that is referred to by the name undefined

With this, internal functions ( a particular representation of the complex number and its companion operations ) can be loaded into the table, and there is no clutter of the global namespace.

#### Message passing
In data-directed programming, using tagged data and generic operations ( in a 2D operation-and-type table) are used to encapsulate logic and integrate separately developed data-type modules.


In the below example, the data-directed make_from_real_imag, dispatches "make_from_real_imag" and "rectangular" to get the make_from_real_imag function from the operation-type table (make_from_real_imag is rectangular only, but a function for getting the real part of a number in rectangular or polar form could be obtained by passing the appropriate data tag.
`data-directed-make-from-real-imag.js`
```
function make_from_real_imag(x, y) {
   return get("make_from_real_imag", "rectangular")(x, y);
}
```
In the message passing example, when applying / calling a generic function, the function's dispatch method is called. Note below make_from_real_imag returns a dispatch function, that will call the specified operation.
`message-passing-make-from-real-imag.js`
```
function make_from_real_imag(x, y) {
    function dispatch(op) {
        return op === "real_part"
            ? x
            : op === "imag_part"
              ? y
              : op === "magnitude"
                ? math_sqrt(square(x) + square(y))
                : op === "angle"
                  ? math_atan(y, x)
                  : error(op,
                          "Unknown op -- make_from_real_imag");
    }
    return dispatch;
}
```

