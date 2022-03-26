---
title: Javascript Event Loop
description: 
published: true
date: 2022-03-26T23:40:55.991Z
tags: front-end, javascript
editor: markdown
---

The event loop is responsible for executing code, collecting and processing events, and executing queued sub-tasks.

![the_javascript_runtime_environment_example.svg](/the_javascript_runtime_environment_example.svg)
(Above image is just theoretical. Modern javascript engines implement and heavily optimized the described semantics).

# Stack
Function calls form a stack of frames.

## Order of Operations examples
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

1. When calling `bar`, a first frame is created containing references to `bar`'s arguments and local variables.

2. When `bar` calls `foo`, a second frame is created and pushed on top of the first one, containing references to `foo`s arguments and local variables.

3. When `foo` returns, the top frame element is popped out of the stack (leaving only `bar`'s call frame). 

4. When `bar` returns, the stack is empty.