---
title: Intermediate React V3
description: 
published: true
date: 2021-11-17T02:35:19.908Z
tags: web-technologies
editor: markdown
---

# useContext
* More emphasis on using sparingly. use of useContext raises questions on where state inside this context comes from. It's difficult to track through an application, and raises questions like, "where is this being tracked" etc. It adds a lot of indirection into your app which is bad. 

# useRef
* Returns a plain JavaScript object. Its value can be accessed and modified (mutability) as many times as you need without worrying about "rerender".
```
function App() {
  const ordinaryObject = { current: 0 } // It will reset to {current:0} at each render
  const refObject = useRef(0) // It will persist (won't reset to the initial value) for the component lifetime
  return <>...</>
}
```
## Common Usecases
* To access the DOM
* Store mutable value like instance variable (in class)

# useReducer
* Alternative to useState. 
* Preferable to useState when you have complex state logic that involves multiple sub-values or when the next state depends on the previous one. 
* You can pass dispatch down instead of callbacks.

# useMemo
* Memoizes expensive function calls so they are only re-evaluated when needed. 