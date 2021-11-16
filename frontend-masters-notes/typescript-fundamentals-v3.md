---
title: Typescript Fundamentals V3
description: 
published: true
date: 2021-11-16T17:44:32.222Z
tags: web-technologies
editor: markdown
---

# Why TypeScript
* Leaves more of your intent in the code. 
* Potential to move some kidns of errors from runtime to compile time
	* Values that are potentially absent
  * Incomplete refactoring
  * Breakage around some internal contracts.
* Great autocomplete

# Breakdown of TypeScript Files
* .ts files contain both type information and code that runs
* .js files contain only code that runs
* .d.ts files contain only type information

# Variables and Values
## Variable Declarations and Inference
```
let age = 6;
```
TypeScript will infer the variable age is a number. If we attempt to reassign age with something besides a number, it will throw an error.
## Literal types
```
const age = 6;
```
Since const values cannot be reassigned, and numbers are immutable, the type of this const is 6, a specific number.

## Implicit any and Type Annotations
```
const RANDOM_WAIT_TIME =
  Math.round(Math.random() * 500) + 500

let startTime = new Date()
let endTime

setTimeout(() => {
  endTime = 0
  endTime = new Date()
}, RANDOM_WAIT_TIME)
```
In the above code, `endTime` is born without a type, so it ends up being an implicit `any`. `any` is the way normal JS variables work, in that you can assign `endTime` to a number, then later a `function`, then a `string`.

If we wanted more safety, we could add a type annotation, such as:

```
let endTime: Date
```

# Function Arguments and Return Values
```
no-type-annotations.js
function add(a, b) {
  return a + b // strings? numbers? a mix?
}
```
```
with-type-annotations.js
function add(a: number, b: number) {
  return a + b // return type will be a number, 
  						// the typescript compiler can infer this
}
```
