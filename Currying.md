---
title: Currying
description: 
published: true
date: 2020-07-27T00:39:53.440Z
tags: 
editor: markdown
---

# Currying

Currying is the technique of converting a function that takes multiple arguments into a series of functions that each only take one argument. 

## Examples

`curry.js`

//uncurried
const add = (a, b) => (a + b);
add(3, 4); // 7

//curried
const add = (a) => ((b) => (a + b));
add(3)(4); // 7