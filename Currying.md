---
title: Currying
description: 
published: true
date: 2020-07-27T00:42:18.593Z
tags: 
editor: markdown
---

# Currying

Currying is the technique of converting a function that takes multiple arguments into a series of functions that each only take one argument. 

## Examples

`//uncurried_add.js`
`const add = (a, b) => (a + b);`
`add(3, 4); // 7`

`//curried_add.js`
`const add = (a) => ((b) => (a + b));`
`add(3)(4); // 7 `