---
title: Recursion
description: 
published: true
date: 2020-08-02T04:33:54.917Z
tags: 
editor: markdown
---

# Recursion

- When a thing is defined in terms of itself or of its type.
- At the machine level, all recursion is implemented as an iterative process for fetching and executing instructions. All function calls are implemented via a runtime stack to keep track of return addresses, actual parameters, and local variables associated with function calls. Returning from a function is accomplished by getting and saving the return address out of the top record on the stack, popping the stack once, and jumping to the saved address.