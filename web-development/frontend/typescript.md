---
title: Typescript
description: 
published: true
date: 2022-08-18T18:20:35.228Z
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
## Equality Narrowing
We can use switch statements or equality checks to compare two values that have some overlap. For example, if one has a type of string bool, and another has string number, if the values are strictly equal, typescript knows that we are dealing with a number.
## In operator Narrowing
Typescript takes into account javascript's `in` operator for determining if an object has a property with a name.
## instanceof Narrowing
Useful for most values constructed with `new`, the js `instanceof` operator is useful for checking whether the prototype chain of a particular variable contains a particular prototype.

For example, `x instanceof Foo` checks whether the prototype chain of `x` contains `Foo.prototype`.

## Control Flow Analysis
Typescript analyzes codes and can (sometimes) determine what conditions must be true when code is executing in a particular place. For example, if a variable can be one of two primitive types, and there is an `if` statement that narrows down that variable and a `return` statement inside that particular block, then typescript will know that after that block that the variable must be the other primitive type. 

## Using Type Predicates
To define a user-defined type guard, we need to define a function whose return type is a `type predicate`. 

```
function isFish(pet: Fish | Bird): pet is Fish {
  return (pet as Fish).swim !== undefined;
}
```
`pet is Fish` is the type predicate for the above example. A predicate takes the form `parameterName is Type`, where `parameterName` must be the name of a parameter from the current function signature.

Any time `isFish` is called with some variable, Typescript will narrow that variable to that specific type if the original type is compatible. 

```
let pet = getSmallPet();
 
if (isFish(pet)) {
  pet.swim();
} else {
  pet.fly();
}
```

You can use the type guard `isFish` to filter an array of `Fish | Bird` and obtain an array of `Fish`. 

## Discriminated Unions
A union of many different interfaces that has a property in common can use that property (the discriminant) to help determine which kind of interface we are dealing with in the union.

## The never type
The `never` type represents a type that shouldn't exist.
### Exhaustiveness Checking
```
type Shape = Circle | Square;
 
function getArea(shape: Shape) {
  switch (shape.kind) {
    case "circle":
      return Math.PI * shape.radius ** 2;
    case "square":
      return shape.sideLength ** 2;
    default:
      const _exhaustiveCheck: never = shape;
      return _exhaustiveCheck;
  }
}
```

IF we add a new member to the `Shape` union,

```
interface Triangle {
  kind: "triangle";
  sideLength: number;
}
 
type Shape = Circle | Square | Triangle;
 
function getArea(shape: Shape) {
  switch (shape.kind) {
    case "circle":
      return Math.PI * shape.radius ** 2;
    case "square":
      return shape.sideLength ** 2;
    default:
      const _exhaustiveCheck: never = shape; // Type 'Triangle' is not assignable to type 'never'.
      return _exhaustiveCheck;
  }
}
```
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

# More on Functions
## Constraints
Sometimes we want to relate two values, but can only operate on a certain subset of values. In this case, we can use a **constraint** to limit the kinds of types that a type parameter can accept.

The below function returns the longer of two values. It's parameter needs to be constrained such that it has a property `length` that is a `number`. That type parameter is constrained using the `extends` clause.

```
function longest<Type extends { length: number }>(a: Type, b: Type) {
  if (a.length >= b.length) {
    return a;
  } else {
    return b;
  }
}
 
// longerArray is of type 'number[]'
const longerArray = longest([1, 2], [1, 2, 3]);
// longerString is of type 'alice' | 'bob'
const longerString = longest("alice", "bob");
// Error! Numbers don't have a 'length' property
const notOK = longest(10, 100);
```

## Guidelines for Writing Good Generic Functions
### Push Type Parameters Down
```
function firstElement1<Type>(arr: Type[]) {
  return arr[0];
}
 
function firstElement2<Type extends any[]>(arr: Type) {
  return arr[0];
}
 
// a: number (good)
const a = firstElement1([1, 2, 3]);
// b: any (bad)
const b = firstElement2([1, 2, 3]);
```

