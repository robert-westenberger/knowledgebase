---
title: Typescript Fundamentals V3
description: 
published: true
date: 2021-11-20T23:39:49.828Z
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
A multi-element, ordered data structure, where position of each item has some special meaning or convention. Typescript is not good at inferring types of tuples.

```
let myCar = [2002, "Toyota", "Corolla"]
```
By default, typescript will infer the above is a mixed array of strings and numbers where order doesn't matter.

The takeaway is, we need to explicitly define when an array should be considered a tuple.
So something like this
```
let myCar: [number, string, string] = [
  2002,
  "Toyota",
  "Corolla",
]
```
#### Limitations
Typescript won't stop us from pushing and popping values from our tuple that would break it. It won't throw any errors even though it should. 

# Structural vs Nominal Types
## What is type checking?
Type checking is answering a question about type equivalence.
### In a function call
```
function foo(x) {
  // ... mystery code ...
}
//
// TYPE CHECKING
// -------------
// Is `myValue` type-equivalent to
//     what `foo` whats to receive?
foo(myValue)
```
### In assignment
```
// is the value y holds type-equivalent to what `x` allows?
x = y
```
### A return
```
const myStrings = ["a"]
/// ---cut---
function bar(): string[] {
  // ...mystery code that might return early...
  //
  //
  // TYPE CHECKING
  // -------------
  // Is `myStrings` type-equivalent to
  //     what `bar` states it will return?
  return myStrings
}
```
## Static vs Dynamic
Static type systems have types in the code and are evaluated as part of the compilation step.

Dynamic type systems have types evaluated at runtime. 

## Nominal vs Structural
### Nominal / Name Based
Compatibility and equivalence of data types is determined by explicit declarations and/or the name of the types.
```
public class Car {
  String make;
  String model;
  int make;
}
public class CarChecker {
  // takes a `Car` argument, returns a `String`
  public static String printCar(Car car) {  }
}
Car myCar = new Car();
// TYPE CHECKING
// -------------
// Is `myCar` type-equivalent to
//     what `checkCar` wants as an argument?
CarChecker.checkCar(myCar);
```
### Structural / Property based
This kind of type system just cares about shape. 
```
class Car {
  make: string
  model: string
  year: number
  isElectric: boolean
}

class Truck {
  make: string
  model: string
  year: number
  towingCapacity: number
}

const vehicle = {
  make: "Honda",
  model: "Accord",
  year: 2017,
}

function printCar(car: {
  make: string
  model: string
  year: number
}) {
  console.log(`${car.make} ${car.model} (${car.year})`)
}

printCar(new Car()) // Fine
printCar(new Truck()) // Fine
printCar(vehicle) // Fine
```

## Duck typing
Gets its name from the phrase
> If it looks like a duck, swims like a duck, and quack like a duck, then it probably is a duck.
Usually to describe dynamic type system. 

# Union and Intersection Types
Can be conceptually thought of as OR or AND operations, respectively.

## Union Types in TypeScript
Union types are described using the | (pipe) operator.

```
function flipCoin(): "heads" | "tails" {
  if (Math.random() > 0.5) return "heads"
  return "tails"
}

const outcome = flipCoin()
```

Another example..

```
function flipCoin(): "heads" | "tails" {
  if (Math.random() > 0.5) return "heads"
  return "tails"
}

function maybeGetUserInfo():
  | ["error", Error]
  | ["success", { name: string; email: string }] {
  if (flipCoin() === "heads") {
    return [
      "success",
      { name: "Mike North", email: "mike@example.com" },
    ]
  } else {
    return [
      "error",
      new Error("The coin landed on TAILS :("),
    ]
  }
}
const outcome = maybeGetUserInfo()
```
In the above, outcome would have the following type..
```
const outcome: ["error", Error] | ["success", {
    name: string;
    email: string;
}]
```

# Interfaces and Type Aliases
Interfaces and type aliases are ways in which we can give our types useful and meaningful names. You should pretty much always prefer interfaces unless you need some specific features (if you need to define something other than an object type).                                   

## Type Aliases
Allow us to 
* Define a more meaningful name for a particular type
* Declare the particulars of the type in a single place
* Import and export this type from modules, the same as if it were an exported value.

```
///////////////////////////////////////////////////////////
// @filename: types.ts
export type UserContactInfo = {
  name: string
  email: string
}

///////////////////////////////////////////////////////////
// @filename: utilities.ts
import { UserContactInfo } from "./types"
function printContactInfo(info: UserContactInfo) {
  console.log(info)

	console.log(info.email)
}
```

## Interfaces
An interface is a way of defining an object type. An "object type" can be thought of as, "an instance of a class could conceivably look like this".

### Inheritance
#### Extends
Regular es6 class inheritance uses the `extends` keyword. For example,
```
class Animal {
  eat(food) {
    consumeFood(food)
  }
}
class Dog extends Animal {
  bark() {
    return "woof"
  }
}
const d = new Dog()
d.eat
d.bark
```

In typescript, a sub-interface extends from a base interface. 
```
interface Animal {
  isAlive(): boolean
}
interface Mammal extends Animal {
  getFurOrHairColor(): string
}
interface Dog extends Mammal {
  getBreed(): string
}
function careForDog(dog: Dog) {
  dog.getBreed
  //   ^|
}
```
#### Implements
Typescript adds a second clause that can be used to state that a given class should produce instances that confirm to a given interface: `implements`.

```
function consumeFood(arg) {}
/// ---cut---
interface AnimalLike {
  eat(food): void
}

class Dog implements AnimalLike {
  bark() {
    return "woof"
  }
}
```
The above will throw an error, since the class Dog doesn't have the eat method required by the AnimalLike interface.

Both `extends` and `implements` can be used together.

```
class LivingOrganism {
  isAlive() {
    return true
  }
}
interface AnimalLike {
  eat(food): void
}
interface CanBark {
  bark(): string
}

class Dog
  extends LivingOrganism
  implements AnimalLike, CanBark
{
  bark() {
    return "woof"
  }
  eat(food) {
    consumeFood(food)
  }
}
```
### Open Interfaces
Typescript interfaces are "open", meaning that unlike in type aliases, you can have multiple declarations in the same scope. If two interface declarations are in the same scope, they are merged together.

### Recursion
```
type NestedNumbers = number | NestedNumbers[]

const val: NestedNumbers = [3, 4, [5, 6, [7], 59], 221]
```

# Functions
## Callable Types
Both type aliases and interfaces offer the capabiltiy to describe call signatures.

```
interface TwoNumberCalculation {
  (x: number, y: number): number
}

type TwoNumberCalc = (x: number, y: number) => number

const add: TwoNumberCalculation = (a, b) => a + b
const subtract: TwoNumberCalc = (x, y) => x - y
```
In the above (the interface TwoNumberCalculation and the type TwoNumberCalc are identical)..
* The return type for an interface is `:number`, and for its type alias it's `=>number`. 
* Because we provide types for the functions `add` and `subtract`, we don't need to provide type annotations for each individual function's argument list or return type.

### void 
`void` is a special type, that's specifically used to describe the return values. A return value from a `void` function is explicitly meant to be ignored.

## Construct signatures
Similar to call signatures, except they describe what should happen with the new keyword.

```
interface DateConstructor {
  new (value: number): Date
}

let MyDateConstructor: DateConstructor = Date
const d = new MyDateConstructor()
```

## Function overloads
Given the following code
```
<iframe src="https://example.com" />
<!-- // -->
<form>
  <input type="text" name="name" />
  <input type="text" name="email" />
  <input type="password" name="password" />
  <input type="submit" value="Login" />
</form>
```

What if we had to create a function that allowed us to register a “main event listener”?
* If we are passed a form element, we should allow registration of a “submit callback”
* If we are passed an iframe element, we should allow registration of a ”postMessage callback”
```
type FormSubmitHandler = (data: FormData) => void
type MessageHandler = (evt: MessageEvent) => void

function handleMainEvent(
  elem: HTMLFormElement,
  handler: FormSubmitHandler
)
function handleMainEvent(
  elem: HTMLIFrameElement,
  handler: MessageHandler
)
function handleMainEvent(
  elem: HTMLFormElement | HTMLIFrameElement,
  handler: FormSubmitHandler | MessageHandler
) {}

const myFrame = document.getElementsByTagName("iframe")[0]
const myForm = document.getElementsByTagName("form")[0]
handleMainEvent(myFrame, (val) => {
})
handleMainEvent(myForm, (val) => { })
```

## this Types
Sometimes we have a free-standing function that has a strong opinion around what `this` will end up being, at the time it is invoked.

For example, if we had a DOM event listener for the button
`
<button onClick="myClickHandler">Click Me!</button>
`

We could define `myClickHandler` as follows:
```
function myClickHandler(event: Event) {
  this.disabled = true
}

myClickHandler(new Event("click")) // seems ok
```
but this will give us a warning because `this` has no type annotation.

Here, we now specify the type correctly, and we give the function exactly the kind of type it wants.
```
function myClickHandler(
  this: HTMLButtonElement,
  event: Event
) {
  this.disabled = true
}
myClickHandler
const myButton = document.getElementsByTagName("button")[0]
const boundHandler = myClickHandler.bind(myButton)
boundHandler(new Event("click")) // bound version: ok
myClickHandler.call(myButton, new Event("click")) // also ok
```

# Classes
## Access Modifier Keywords
`public`, `private`, and `protected`

$$
\begin{array}{ll}
\text { keyword } & \text { who can access } \\
\hline \text { public } & \text { everyone (this is the default) } \\
\hline \text { protected } & \text { the instance itself, and subclasses } \\
\hline \text { private } & \text { only the instance itself }
\end{array}
$$

## JS private #fields
denoted by the hash prefix
```
class Car {
  public make: string
  public model: string
  #year: number

  constructor(make: string, model: string, year: number) {
    this.make = make
    this.model = model
    this.#year = year
  }
}
const c = new Car("Honda", "Accord", 2017)
```
`c.#year` will throw an error because its private, hence not accessible outside of the car class.
## readonly
Can be used with other keywords. Will throw an error if you try to reassign the value. Giving it an initial value in a constructor is fine. 

## Param Properties
Before using param properties...
```
class Car {
  make: string
  model: string
  year: number
  constructor(make: string, model: string, year: number) {
    this.make = make
    this.model = model
    this.year = year
  }
}
```

After using param properties..
```
class Car {
  constructor(
    public make: string,
    public model: string,
    public year: number
  ) {}
}

const myCar = new Car("Honda", "Accord", 2017)
myCar.make
```


# Top and Bottom Types
## Top Types
A top type is a type that describes any possible value allowed by the system. In set theory notation, this would be $\{x \mid x$ could be anything $\}$.

Typescript provides two of these types: `any` and `unknown`.
### any
As described previously, `any` is just the default javascript type. A variable with an any type can be assigned any type of value.

### unknown
Like `any`, `unknown` can accept any value, but its different in a very important way..

Values with an `unknown` type cannot be used without first applying a type guard.

So the below would throw an error
```
let myUnknown: unknown = 14
myUnknown.it.is.possible.to.access.any.deep.property
```

### Practical Use of Top Types
When converting a project from javascript to typescript, its convenient to be able to incrementally add increasingly strong types. A lot of things will be `any` until you get a chance to inspect and add more specific types.

`unknown` is great for vals received at runtime ( API calls / the data layer). By obligating consumers of these values to perform some light validation before using them, errors are caught earlier, and can often be surfaced with more context.


## Bottom Type - Never
A bottom type is a type that describes no possible value allowed by the system. 
### Use case
##### Exhaustive Conditionals
```
class Car {
  drive() {
    console.log("vroom")
  }
}
class Truck {
  tow() {
    console.log("dragging something")
  }
}
type Vehicle = Truck | Car

let myVehicle: Vehicle = obtainRandomVehicle()

// The exhaustive conditional
if (myVehicle instanceof Truck) {
  myVehicle.tow() // Truck
} else if (myVehicle instanceof Car) {
  myVehicle.drive() // Car
} else {
  // NEITHER!
  const neverValue: never = myVehicle
}
```

# Type Guards and Narrowing
## Built-in Type Guards
There are a bunch of type guards that are included with TypeScript. Below is an illustrative example of a wide variety of them. 
```
let value:
  | Date
  | null
  | undefined
  | "pineapple"
  | [number]
  | { dateRange: [Date, Date] }

// instanceof
if (value instanceof Date) {

}
// typeof
else if (typeof value === "string") {

}
// Specific value check
else if (value === null) {

}
// Truthy/falsy check
else if (!value) {
}
// Some built-in functions
else if (Array.isArray(value)) {

}
// Property presence check
else if ("dateRange" in value) {

} else {

}
```

## User-defined Type Guards
### value is foo
The `is` type guard is meant to work in cooperation with a control flow statement of some sort, to indicate that different branches of the "flow" will be taken based on an evaluation of a variable's type.

Below is an example of using built-in typeguards to narrow the type of a particular variable.

```
interface CarLike {
  make: string
  model: string
  year: number
}

let maybeCar: unknown

// the guard
function isCarLike(valueToTest: any) {
  return (
    valueToTest &&
    typeof valueToTest === "object" &&
    "make" in valueToTest &&
    typeof valueToTest["make"] === "string" &&
    "model" in valueToTest &&
    typeof valueToTest["model"] === "string" &&
    "year" in valueToTest &&
    typeof valueToTest["year"] === "number"
  )
}

// using the guard
if (isCarLike(maybeCar)) {
  //maybeCar will be unknown
}
```

Below, we are using the `is` typeguard. Now, `isCarLike`'s return tpype will be CarLike.
```
interface CarLike {
  make: string
  model: string
  year: number
}

let maybeCar: unknown

// the guard
function isCarLike(
  valueToTest: any
): valueToTest is CarLike {
  return (
    valueToTest &&
    typeof valueToTest === "object" &&
    "make" in valueToTest &&
    typeof valueToTest["make"] === "string" &&
    "model" in valueToTest &&
    typeof valueToTest["model"] === "string" &&
    "year" in valueToTest &&
    typeof valueToTest["year"] === "number"
  )
}

// using the guard
if (isCarLike(maybeCar)) {
  //maybeCar will be CarLike
}
```

### asserts value is Foo
Another approach that eliminates the need for a conditional. 

```
interface CarLike {
  make: string
  model: string
  year: number
}

let maybeCar: unknown

// the guard
function assertsIsCarLike(
  valueToTest: any
): asserts valueToTest is CarLike {
  if (
    !(
      valueToTest &&
      typeof valueToTest === "object" &&
      "make" in valueToTest &&
      typeof valueToTest["make"] === "string" &&
      "model" in valueToTest &&
      typeof valueToTest["model"] === "string" &&
      "year" in valueToTest &&
      typeof valueToTest["year"] === "number"
    )
  )
    throw new Error(
      `Value does not appear to be a CarLike${valueToTest}`
    )
}

// using the guard
maybeCar // maybeCar is unknown
assertsIsCarLike(maybeCar)
maybeCar // maybeCar is CarLike
```

In the above example, if `assertsIsCarLike` throws an error, it should be taken as an indication that `valueToTest` is NOT type-equivalent to `CarLike`.

Therefore, if we get past the assertion and keep executing code on the next line, the type changes from `unknown` to `CarLike`.

## Writing High Quality Guards
Below is a **BAD EXAMPLE** of a type guard..
```
function isNull(val: any): val is null {
  return !val
}

const empty = ""
const zero = 0
if (isNull(zero)) {
  console.log(zero) // it is possible to get here ( 0 is falsy)
}
if (isNull(empty)) {
  console.log(empty) // its possible to get here (empty string is falsy)
}
```
> Common mistakes like forgetting about the possibilities of strings and numbers being falsy can create false confidence in the correctness of your code. {.is-info}

> “Untruths” in your type guards will propagate quickly through your codebase and cause problems that are quite difficult to solve. {.is-info}

> In cases where the rest of your code relies on a particular value being of a certain type, make sure to throw an error so that unexpected behavior is **LOUD** instead of quiet.
{.is-info}

# Nullish Values
## null
There is a value, and that value is nothing. 
## undefined
The value isn't available yet
## void
Exclusively used to describe that a function's return 

# Generics
