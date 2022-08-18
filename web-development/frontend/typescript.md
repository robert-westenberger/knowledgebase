---
title: Typescript
description: 
published: true
date: 2022-08-18T16:45:11.454Z
tags: typescript
editor: markdown
---

# Types vs Interfaces
## Use Interfaces Over Type Aliases
You will get better error messages.
## Interfaces are Open, Type Aliases are Closed
This means you can extend an interface by declaring it a second time.

```
interface Kitten {
  purrs: boolean;
}

interface Kitten {
  colour: string;
}

const pretty_kitty: Kitten = {
  purrs: true,
  colour: 'red'
}
```

A type cannot be changed outside of it's declaration.

```
type Puppy = { // this errors
  color: string;
};

type Puppy = { // this errors
  toys: number;
};
```
## Interfaces may only be used to declare the shapes of objects, not rename primitives
```
// This isn't feasible with interfaces
interface X extends string {

}
```
# Narrowing
When working with union types, typescript will allow an operation iff it is valid for every member of the union. 

You can narrow the union with code. Narrowing occurs when TS can deduce a more specific type for a value based on the structure of the code. 
## typeof type guards
We can use the `typeof` operator to get the primitive type of a variable and execute behavior depending on what the typeof returns. For example, if we test that a variable is a string, any string operations on that variable within that particular if block will be supported.
## Truthiness Narrowing
IF something is of type string for example, we can test it's truthiness to confirm it's not an empty string, so we can be sure a particular is passed a nonempty string. 

Another example is to test that an array is not null or undefined before iterating over it.
# Type Assertions
For example, if you’re using `document.getElementById`, TypeScript only knows that this will return some kind of `HTMLElement`, but you might know that your page will always have an `HTMLCanvasElement` with a given ID.

In this situation, you can use a type assertion to specify a more specific type:
```
const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;
```

TypeScript only allows type assertions which convert to a more specific or less specific version of a type. This rule prevents “impossible” coercions like:

```
const x = "hello" as number;
```

