---
title: Typescript
description: 
published: true
date: 2022-08-18T20:07:10.628Z
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
### Use Fewer Type Parameters
```
function filter1<Type>(arr: Type[], func: (arg: Type) => boolean): Type[] {
  return arr.filter(func);
}
 
function filter2<Type, Func extends (arg: Type) => boolean>(
  arr: Type[],
  func: Func
): Type[] {
  return arr.filter(func);
}
```

We’ve created a type parameter `Func` that doesn’t relate two values. That’s always a red flag, because it means callers wanting to specify type arguments have to manually specify an extra type argument for no reason. `Func` doesn’t do anything but make the function harder to read and reason about!

## Function Overloads
```
function makeDate(timestamp: number): Date;
function makeDate(m: number, d: number, y: number): Date;
function makeDate(mOrTimestamp: number, d?: number, y?: number): Date {
  if (d !== undefined && y !== undefined) {
    return new Date(y, mOrTimestamp, d);
  } else {
    return new Date(mOrTimestamp);
  }
}
const d1 = makeDate(12345678);
const d2 = makeDate(5, 5, 5);
const d3 = makeDate(1, 3);
```

# Object Types
## Index Signatures
Sometimes you don’t know all the names of a type’s properties ahead of time, but you do know the shape of the values.

In those cases you can use an index signature to describe the types of possible values, for example:

```
interface StringArray {
  [index: number]: string;
}
 
const myArray: StringArray = getStringArray();
const secondItem = myArray[1];
```

The above `StringArray` interface has an index signatue. It states that when `StringArray` is indexed with a `number`, it wil return a `string`. An index signature property type must either be `string` or `number`.

The following will give an error
```
interface NumberDictionary {
  [index: string]: number;
 
  length: number; // ok
  name: string; // Property 'name' of type 'string' is not assignable to 'string' index type 'number'.
}
```  

However, properties of different types are acceptable if the index signature is a union of the property types:
```
interface NumberOrStringDictionary {
  [index: string]: number | string;
  length: number; // ok, length is a number
  name: string; // ok, name is a string
}
```

## Extending Types
```
interface BasicAddress {
  name?: string;
  street: string;
  city: string;
  country: string;
  postalCode: string;
}
 
interface AddressWithUnit extends BasicAddress {
  unit: string;
}
```

### Extending (Multiple) Types
```
interface Colorful {
  color: string;
}
 
interface Circle {
  radius: number;
}
 
interface ColorfulCircle extends Colorful, Circle {}
 
const cc: ColorfulCircle = {
  color: "red",
  radius: 42,
};
```

## Generic Object Types
We can make a generic `Box` that takes a type parameter

```
interface Box<Type> {
  contents: Type;
}
```

### Generic Constraints
```
function loggingIdentity<Type>(arg: Type): Type {
  console.log(arg.length); // ERROR: Property 'length' does not exist on type 'Type'.
  return arg;
}
```

We'd like to constrain this function to work with any and all types that **also** have the `.length` property. 

```
interface Lengthwise {
  length: number;
}
 
function loggingIdentity<Type extends Lengthwise>(arg: Type): Type {
  console.log(arg.length); // Now we know it has a .length property, so no more error
  return arg;
}
```

Because the generic function is now constrained, it will no longer work over any and all types.

### Using Type Parameters in Generic Constraints
You can declare a type param that is constrained by another type param. For example, below we'd like to get a property from an object given it's name. 
```
function getProperty<Type, Key extends keyof Type>(obj: Type, key: Key) {
  return obj[key];
}
 
let x = { a: 1, b: 2, c: 3, d: 4 };

getProperty(x, "a");
getProperty(x, "m"); // Argument of type '"m"' is not assignable to parameter of type '"a" | "b" | "c" | "d"'.
```

# keyof type operator
The `keyof` operator takes an object type and produces a string or numeric literal union of its keys. 

The following type `P` is the same type as `"x"|"y"`. 

```
type Point = { x: number; y: number };
type P = keyof Point;
```

If the type has a `string` or `number` index sig, `keyof` will return those types instead.

```
type Arrayish = { [n: number]: unknown };
type A = keyof Arrayish; // A=number

type Mapish = { [k: string]: boolean };
type M = keyof Mapish; // M = string | number
```

# typeof type operator
```
function f() {
  return { x: 10, y: 3 };
}
type P = ReturnType<typeof f>; // type P = {x:number; y: number;}
```
# Indexed Access Types
```
type Person = { age: number; name: string; alive: boolean };
type Age = Person["age"]; // type Age = number
```

```
type I2 = Person[keyof Person]; // type I2 = string | number | boolean
```

```
const MyArray = [
  { name: "Alice", age: 15 },
  { name: "Bob", age: 23 },
  { name: "Eve", age: 38 },
];
 
type Person = typeof MyArray[number]; // type Person = { name: string; age: number; }
```

You can only use types when indexing, meaning you can’t use a const to make a variable reference:

```
const key = "age";
type Age = Person[key]; // ERROR! 'key' refers to a value
```

However, you can use a type alias for a similar style of refactor:
```
type key = "age";
type Age = Person[key];
```

# Conditional Types
Conditional types take a form that looks a little like conditional expressions (`condition ? trueExpression : falseExpression`) in JavaScript:

```
  SomeType extends OtherType ? TrueType : FalseType;
```

## Example (Without conditional types)
```
interface IdLabel {
  id: number /* some fields */;
}
interface NameLabel {
  name: string /* other fields */;
}
 
function createLabel(id: number): IdLabel;
function createLabel(name: string): NameLabel;
function createLabel(nameOrId: string | number): IdLabel | NameLabel;
function createLabel(nameOrId: string | number): IdLabel | NameLabel {
  throw "unimplemented";
}
```

## Example (With Conditional Types)
```
type NameOrId<T extends number | string> = T extends number
  ? IdLabel
  : NameLabel;

function createLabel<T extends number | string>(idOrName: T): NameOrId<T> {
  throw "unimplemented";
}

let a = createLabel("typescript");

let b = createLabel(2.8);

let c = createLabel(Math.random() ? "hello" : 42);
```

### Conditional Type Constraints
```
type MessageOf<T extends { message: unknown }> = T["message"];
 
interface Email {
  message: string;
}
 
type EmailMessageContents = MessageOf<Email>; // type EmailMessageContents = string
```

What if we wanted `MessageOf` to take any type, and default to something like `never` if a `message` property isn't available? We can do this by moving the constraint out and introducing a conditional type:

```
type MessageOf<T> = T extends { message: unknown } ? T["message"] : never;
 
interface Email {
  message: string;
}
 
interface Dog {
  bark(): void;
}
 
type EmailMessageContents = MessageOf<Email>;
type DogMessageContents = MessageOf<Dog>;
```

## Inferring Within Conditional Types
Conditional types provide us with a way to `infer` from types we compare against in the true branch using the infer keyword.