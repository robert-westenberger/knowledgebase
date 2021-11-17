---
title: Typescript Fundamentals V3
description: 
published: true
date: 2021-11-17T17:07:01.105Z
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

## Function Arguments and Return Values
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

# Objects, Arrays and Tuples
## Objects
Object types are defined by:
* The names of the properties that may or may not be present
* The types of those properties
## Optional Properties
We can denote an object property is optional by using the `?` operator.
```
let car: {
  make: string
  model: string
  year: number
  chargeVoltage?: number
}
```
## Excess Property Checking
```
function printCar(car: {
  make: string
  model: string
  year: number
  chargeVoltage?: number
}) {
  // implementation removed for simplicity
}

printCar({
  make: "Tesla",
  model: "Model 3",
  year: 2020,
  chargeVoltage: 220,
  color: "RED", // <0------ EXTRA PROPERTY
  })
```
In the above code, `color` will throw an error since it's not defined in the  `car` parameter object's type declaration. 

## Index Signatures
Representing a type for dictionaries, where values of a consistent type are retrievable by keys.
```
const phones: {
  [k: string]: {
    country: string
    area: string
    number: string
  }
} = {}

const phones = {
  home: { country: "+1", area: "211", number: "652-4515" },
  work: { country: "+1", area: "670", number: "752-5856" },
  fax: { country: "+1", area: "322", number: "525-4357" },
}
```
## Array Types
```
const fileExtensions = ["js", "ts"];
```
Typescript is smart enough to infer that the above is an array of strings.
```
const cars = [{
    make: "Toyota",
    model: "Corolla",
    year: 2002,
  },
]
```
Above will be typed as an array of objects, where the make and model keys are required and are strings, and the year is required and is a number.

### Tuples
A multi-element, ordered data structure, where position of each item has some special meaning or convention.