---
title: Programming Puzzles
description: 
published: true
date: 2023-03-21T20:59:41.880Z
tags: 
editor: markdown
---

# Implement Curry

Currying is a useful technique used in JavaScript applications.

Please implement a curry() function, which accepts a function and return a curried one.

Here is an example


```
const join = (a, b, c) => {
   return `${a}_${b}_${c}`
}

const curriedJoin = curry(join)

curriedJoin(1, 2, 3) // '1_2_3'

curriedJoin(1)(2, 3) // '1_2_3'

curriedJoin(1, 2)(3) // '1_2_3'
```
## Implementation
```
function curry(fn) {
  return function curriedFn(...args) {
    if (args.length === fn.length) {
      return fn(...args);
    }
    return function(...partial) {
        return curriedFn(...args, ...partial);
      }
  }
}
```