---
title: Section 2.5 Systems with Generic Operations
description: 
published: true
date: 2020-11-24T18:10:37.237Z
tags: book-notes
editor: markdown
---

# Systems with Generic Operations
Using tagged data and layers of generic operations, we can design systems that handle operations that are generic over different representations and with differing arguments.
Tags can be attached to data objects in layers that will tell the system how the data will be routed within it. A generic complex number system might expose the operations add, subtract, multiply, and divide; and those operations will use an operation table to lookup more specific operations. To calculate the addition of two complex numbers for example, the add function would be passed a "complex" tag, which directs it to the complex package. The complex package would look for a "rectangular" tag, directing it for further dispatching.

**Coercion** is where objects of one type are represented as being of another type.For example, an ordinary number can be seen as a complex number whos imaginary part is 0. Coercion makes it possible to perform operations on differing types of data (for example, adding a regular number and a complex number) by coercing the type of one object to that of the subsequest object (if a coercion function is implemented) and then the generic operation on two like data objects can be performed. 

