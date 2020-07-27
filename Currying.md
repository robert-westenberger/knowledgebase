---
title: Currying
description: 
published: true
date: 2020-07-27T01:08:27.278Z
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



### Related Exercises
#### SICP JS 2.20
*Write a function **brooks**, that takes a curried function as first argument then as second argument a list of arguments to which the current function is then applied, one by one, in the given order.*

*For example, the following application of **brooks** should have the same effect as* `add(3)(4) // curried add`

`brooks(plus_curried, list(3, 4));`

*Also write a curried version of **brooks***.

Lastly, what are the results of evaluating the following two statements?

`brooks_curried(list(brooks_curried,
                    list(plus_curried, 3, 4)));`
`
brooks_curried(list(brooks_curried,
                    list(brooks_curried, 
                         list(plus_curried, 3, 4))));`
                         
              
---
