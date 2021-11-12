---
title: Complete Intro to React v6
description: 
published: true
date: 2021-11-12T17:53:53.664Z
tags: web-technologies, react
editor: markdown
---

# What React is 
* A library for the view layer.
* Declarative ( you say what you want, not how to get there. It's essentially just another layer of abstraction ).
* Component based 

# Hooks
* Functions that let you "hook into" React state and lifecycle features from function components.
* Never put hooks in a for loop, if statement, etc.

## useState
* Lets you use state without writing a class
* Probably most commonly used hook
* useState returns a tuple: the current state value and a function that lets you update it.
* The only argument to useState is the initial state.
## useEffect
* Handles side effects (data fetching, subscriptions, manually changing the DOM from React components).
* Serves the same purpose as componentDidMount, componentDidUpdate, componentWillUnmount, but unified into a single API.