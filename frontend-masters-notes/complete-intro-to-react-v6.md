---
title: Complete Intro to React v6
description: 
published: true
date: 2021-11-14T00:31:54.293Z
tags: web-technologies, react
editor: markdown
---

# What React is 
* A library for the view layer.
* Declarative ( you say what you want, not how to get there. It's essentially just another layer of abstraction ).
* Component based 

# Hooks
* Functions that let you "hook into" React state and lifecycle features from function components.
* Never put hooks in a for loop, if statement, etc. (only call hooks at the top level)
* Hooks solves problems formerly solved by HOCs and render props.
## useState
* Lets you use state without writing a class
* Probably most commonly used hook
* useState returns a tuple: the current state value and a function that lets you update it.
* The only argument to useState is the initial state.
## useEffect
* Handles side effects (data fetching, subscriptions, manually changing the DOM from React components).
* Serves the same purpose as componentDidMount, componentDidUpdate, componentWillUnmount, but unified into a single API.
* Effects may optionally specify how to "clean up" after them by returning a function. 

## Custom Hooks
* For common pieces of functionality in your application.
