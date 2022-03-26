---
title: Javascript Interview Questions
description: 
published: true
date: 2022-03-26T23:31:02.730Z
tags: interviewing, javascript
editor: markdown
---

# What is event delegation?
A technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant element due to event bubbling up the DOM.

For example, instead of attaching an event indidvidually to each `<li>` in a list, you could attach it to just the `<ul>` and then check for the event target to see which list item was clicked.

# How does the javascript event loop work?
Javascript has a runtime model based on an event loop, which is responsible for executing the code, collecting and processing events, and executing queued sub-tasks. 

Remember that javascript is single-threaded. 
# Explain how `this` works in Javascript
1. If the `new` keyword is used when calling the function, `this` inside the function is a brand new object. 
2. If `apply`, `call`, or `bind` are used to call/create a function, `this` inside the function is the object that is passed in as the arugment.
3. If a function is called as a method, such as `obj.method()`-`this` is the object that the function is a property of.
4. If a function is invoked as a free function invocation, meaning it was invoked without any of the conditions present above, `this` is the global object. In a browser, its the `window` object. If in strict mode, it will be undefined instead of the window object.
5. If multiple of the above rules apply, the rule that is higher wins and will set the `this` value.
6. If the function is an ES2015 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created.

# Can you give an example of one of the ways that working with `this` has changed in ES6?
ES6 allows you to use arrow functions which uses the enclosing lexical scope. Arrow functions establish `this` based on the scope the Arrow function is defined within. They shouldn't be used for methods on objects for this reason.

# Explain how prototypal inheritance works
All javascript objects have a `__proto__` property (with the exception of objects created with `__Object.create(null)__`, that is a reference to another object called it's prototype. When a property is accessed on an object and if the property is not found on that object, the Javascript engine will traverse down this prototype chain looking for that property. 

Note that the `class` keyword is just syntactical sugar, and javascript is still prototypal.

# What's the difference between a variable that is: `null`, `undefined`, or undeclared?
## Undeclared
Created when you assign a value to an identifier that is not previously created using `var`, `let`, or `const`. Undeclared vars will be defined globally, outside of the current scope. In strict mode, a `ReferenceError` will be thrown when you try to assign to an undeclared variable. 
## `undefined`
A variable that is `undefined` is a variable that has been declared, but not assigned a value. If a function does not return any value as the result of executing it is assigned to a variable, the variable also will be `undefined`. 
## `null` 
A variable that is `null` will have been explicitly assigned to the `null` value. It represents no value and is different from `undefined` in the sense that it has been explicitly assigned.

# What is a closure?
A closure is the combination of a function and the lexical environment within which that function was declared. A closure gives you access to an outer function's scope from an inner function. 

# How / why would you use a closure?
* Data privacy / emulating private methods with closures.
* Partial Applications or currying

# What's a typical use case for anonymous functions?
They can be used in IIFEs to encapsulate some code within a local scope so that vars declared in it do not leak to the global scope. 

They can be used as callback functions. 

# How do you organize your code? 
React/Redux encourages a single-direcitonal data flow based on Flux architecture. The app's models are represented as plain objects that are manipulated by pure functions. State is manipulated using actions and reducers like in any other redux application.

# Why can we modify a key inside an object which was declared with a const variable?
Because it's mutating the content of the object, not reassigning the variable itself. 

To prevent the mutation of an object is another concern entirely. You need something like `Object.freeze()`. 
