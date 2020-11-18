---
title: Section 2.5 Systems with Generic Operations
description: 
published: true
date: 2020-11-18T19:29:34.495Z
tags: book-notes
editor: markdown
---

# Systems with Generic Operations
Using tagged data and layers of generic operations, we can design systems that handle operations that are generic over different representations and with differing arguments.
Tags can be attached to data objects in layers that will tell the system how the data will be routed within it. A generic complex number system might expose the operations add, subtract, multiply, and divide; and those operations will use an operation table to lookup more specific operations. To calculate the addition of two complex numbers for example, the add function would be passed a "complex" tag, which directs it to the complex package. The complex package would look for a "rectangular" tag, directing it for further dispatching..

