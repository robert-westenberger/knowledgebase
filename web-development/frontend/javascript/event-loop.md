---
title: Javascript Event Loop
description: 
published: true
date: 2022-03-26T23:38:04.980Z
tags: front-end, javascript
editor: markdown
---

The event loop is responsible for executing code, collecting and processing events, and executing queued sub-tasks.

![the_javascript_runtime_environment_example.svg](/the_javascript_runtime_environment_example.svg)
(Above image is just theoretical. Modern javascript engines implement and heavily optimized the described semantics).

# Stack
Function calls form a stack of frames.

```
function foo(b) {
  let a = 10
  return a + b + 11
}

function bar(x) {
  let y = 3
  return foo(x * y)
}

const baz = bar(7) // assigns 42 to baz
```