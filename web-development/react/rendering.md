---
title: React Rendering
description: 
published: true
date: 2022-02-22T19:21:52.485Z
tags: react, web-framework
editor: markdown
---

(Notes from https://blog.isquaredsoftware.com/2020/05/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior/)

# Render and Commit Phases
Note that rendering is not the same thing as "updating the DOM".
## Render
React will start at the root of the component tree and recursively loop downwards, finding all components that have been flagged as needing updates. For each flagged component, React will call that component's render method. The render method will output how that particular component will look like in the DOM, given its props and state at the time of the render.

React will then do a diff of the new tree of objects (sometimes referred to as the "virtual DOM"). When doing this, React will collect a list of all changes that need to be applied to make the real DOM look like the current desired output.
## Commit
After the render phase above, react will now take the list of required changes that need to be applied and apply them to the actual DOM.

# How Does React Handle Renders?
## Queuing Renders
After the initial render has completed, there are a few different ways to tell React to queue a re-render

Class components (this.setState(), this.forceUpdate())
Function components (useState, useReducer)

or calling ReactDOM.render(<App />), which is equivalent to calling forceUpdate() on the root component

## Standard Render Behavior
When a parent component renders, React will recursively render all child components inside of it. 
In this case (in normal rendering), React doesn't care whether "props changed".. it will render child components unconditionally just because the parent rendered.

## Rules of React Rendering
### Things to Avoid (in render logic)
* Don't mutate existing variables and objects.
* Don't create randomized values like `Math.random()` or `Date.now()`
* Don't make network requests
* Don't queue state updates
### Things that may occur (in render logic)
* Mutate objects that were newly created while rendering.
* Throw errors
* "Lazy initialize" data that hasn't been created yet, such as a cached value.

## Component Types and Reconciliation

During the render process, React will compare elements based on their type field first. IF an element in a given spot in the component tree changes to a different type (like going from `<div>` to `<span>`, or `<ComponentA>` to `<ComponentB>`, React will assume that the entire tree has changed, destroying the entire existing component tree section, including all DOM nodes, and recreating it from scratch with new component instances.

So **NEVER** do this

```
function ParentComponent() {
  // This creates a new `ChildComponent` reference every time!
  function ChildComponent() {}
  
  return <ChildComponent />
}
```

Always define components separately

```
  // This only creates one component type reference
function ChildComponent() {}
  
function ParentComponent() {

  return <ChildComponent />
}
```

## Keys and Reconciliation
React uses they `key` pseudo-prop as a unique identifier to differentiate specific instances of a component type. 

Keys are especially important here if you are rendering data that may be changed in some way, such as reordering, adding, or deleting list entries.

It's important that keys should be some kind of unique IDs from your data if possible. 

Keys are useful for component instance identity beyond lists as well. You can add a key to any React component at any time to indicate its identity, and changing that key will cause React to destroy the old component instance and DOM and create new ones. A common use case for this is a list + details form combination, where the form shows the data for the currently selected list item. Rendering `<DetailForm key={selectedItem.id}>` will cause React to destroy and re-create the form when the selected item changes, thus avoiding any issues with stale state inside the form.
  
## Render Batching and Timing
**Render batching** is when multiple calls to setState() result in a single render pass being queued and executed, usually on a slight delay. (React does this as an optimization).

# Improving Rendering Performance