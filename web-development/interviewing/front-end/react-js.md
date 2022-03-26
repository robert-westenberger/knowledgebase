---
title: React Interview Questions
description: 
published: true
date: 2022-03-26T19:45:01.871Z
tags: react, interviewing, front-end
editor: markdown
---

# What is React and how does it work?
React is a frontend view library created to build complex interactive UIs.

React creates a virtual DOM in memory, and is synced with the "real" DOM by a library such as ReactDOM.

React is declarative. You tell React what state the UI should be in, and it makes sure the DOM matches that state.

# What is the use of `refs`
They provide a way to access DOM nodes or React elements created in the render method. They should be avoided in most cases, however they can be useful when we need direct access to DOM element or an instance of a component. 

## Use cases
- Managing focus, text selection, or media playback
- Triggering imperative animations
- Integrating with third-party DOM libraries

# What is JEST 
Javascript unit testing framework made by facebook based on Jasmine and provides automated mock creation and a jsdom environment. Often used for testing react components.

# What is `props` in React?
Data passed down from parent to child components. When props change, it triggers another rerender. 

# What are the advantages of React?
- Increase performance with Virtual DOM
- JSX makes code easy to read and write
- Renders on both client and server

# What are the major features of React?
- The Virtual DOM
- Unidirectional data flow
- Reusable / Composable UI components

# What is Context? 
Provides a way to pass data through the component tree without having to drill props at every level. 

It's designed to share data that can be considered "global" for a tree of React components.
## Usecases for context
- Current authenticated user
- Theme
- Preferred language

# What are the differences between a class component and a functional component?
## Class Comonents
- Uses ES6 class syntax and the lifecycle methods
- Extend from React.Comonent
- You have to use the `this` keyword to access the props and functions that you declare inside the component

## Functional Components
- Simpler than class based components
- Mainly focus on the UI of an applicaction, not the behavior
- These are basically just the render function in the class component
- Can have state and mimic lifecycle events using hooks

