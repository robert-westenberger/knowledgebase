---
title: Typescript
description: 
published: true
date: 2022-08-18T16:36:02.480Z
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