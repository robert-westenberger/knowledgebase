---
title: Javascript Event Loop
description: 
published: true
date: 2022-03-26T23:59:36.487Z
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

# Heap
Objects are allocated in a heap which is just a name to denote a large, mostly unstructured, region of memory.

# Queue
A javascript runtime uses a message queue, which is a list of messages to be processed. Each message has an associated function that gets called to handle the message.

At some point during the event loop, the runtime starts handling messages on the queue, starting with the oldest. The message is removed from the queue and its corresponding function is called with the message as an input parameter.

Processing of functions continues until the stack is empty. 

# Event Loop
Usually implemented as 
```
while (queue.waitForMessage()) {
  queue.processNextMessage()
}
```
## Run-to-completion
Each message is processed completely before any other message is processed. 

This means that whenever a function is run, it can't be interrupted by another function. This also means that, if a synchronous function takes too long to complete, the web app won't be able to process any other actions, such as a mouse click or scroll.

## Adding Messages
In web browsers, messages are added anytime an event occurs and there is an event listener attached to it. 

### setTimeout
Called with two arguments: a message to add to the queue, and a time value. The time value represents the minimum delay after which the message will be pushed into the queue. 

If there are other messages in the queue after the delay, those other messages will have to be processed before the setTimeout is executed. 

## Several runtimes communicating together 