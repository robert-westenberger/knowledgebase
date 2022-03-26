---
title: React Interview Questions
description: 
published: true
date: 2022-03-26T19:40:38.224Z
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