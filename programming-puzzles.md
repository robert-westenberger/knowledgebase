---
title: Programming Puzzles
description: 
published: true
date: 2023-03-22T03:00:22.958Z
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

# Implement Basic Throttle
Throttling is a common technique used in Web Application, in most cases using lodash solution would be a good choice.

could you implement your own version of basic throttle()?

In case you forgot, throttle(func, delay) will return a throttled function, which will invoke the func at a max frequency no matter how throttled one is called.

Here is an example.

Before throttling we have a series of calling like

─A─B─C─ ─D─ ─ ─ ─ ─ ─ E─ ─F─G

After throttling at wait time of 3 dashes

─A─ ─ ─C─ ─ ─D ─ ─ ─ ─ E─ ─ ─G

Be aware that

call A is triggered right way because not in waiting time
function call B is swallowed because B, C is in the cooling time from A, and C is latter.
## Implementation
- Initialize a variable `throttleTimer` to `false` and `lastArgs` to an empty array.
- Return an anonymous function 
  - if the throttleTimer is false
```
export function throttle<T extends (...args:any[]) => any>(func: T, wait: number): T {

  let throttleTimer = false;
  let lastArgs: any = null;
  return function(...args) {
   
    if (!throttleTimer) {
      func(...args);
      throttleTimer = true;
      const timeout = () => setTimeout(() => {
        throttleTimer = false;
        if (lastArgs) {
          func(...lastArgs);
          throttleTimer = true;
          lastArgs = null;
          timeout();
        }
      }, wait);
      timeout();
    } else {
      lastArgs = args;
    }
  } as T;
}
```
