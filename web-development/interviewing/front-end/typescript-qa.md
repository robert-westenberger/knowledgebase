---
title: Typescript Questions
description: 
published: true
date: 2022-03-26T20:33:28.100Z
tags: typescript, interviewing
editor: markdown
---

# What are generics?
They provide a way to create reusable components. They provide a way to make components work with any data type and not restrict to one data type. 

It is a way to introduce type-safety into components that accept arguments and return values whose type will be indeterminate until they are consumed later in your code. 

# Classes vs Interfaces
## Class
Just an enhancement of the ES6 `class` with type-checking and `static` properties. 
### When to use
It's essentially an object factory ( a blueprint of what an object is supposed to look like and then implemented). 
## Interface
Virtual structure that only exists within the context of typescript. Once code is transpiled to it's target language, interfaces will be stripped from the code. 
### When to use
When we don't need to create an instance of a custom object. 