---
title: Javascript Interview Questions
description: 
published: true
date: 2022-03-26T16:12:27.626Z
tags: interviewing, javascript
editor: markdown
---

# What is event delegation?
A technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant element due to event bubbling up the DOM.

For example, instead of attaching an event indidvidually to each `<li>` in a list, you could attach it to just the `<ul>` and then check for the event target to see which list item was clicked.

# Explain how `this` works in Javascript
1. If the `new` keyword is used when calling the function, `this` inside the function is a brand new object. 
2. If `apply`, `call`, or `bind` are used to call/create a function, `this` inside the function is the object that is passed in as the arugment.
3. If a function is called as a method, such as `obj.method()`-`this` is the object that the function is a property of.
4. If a function is invoked as a free function invocation, meaning it was invoked without any of the conditions present above, `this` is the global object. In a browser, its the `window` object. If in strict mode, it will be undefined instead of the window object.
5. If multiple of the above rules apply, the rule that is higher wins and will set the `this` value.
6. If the function is an ES2015 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created.