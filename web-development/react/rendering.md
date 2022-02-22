---
title: React Rendering
description: 
published: true
date: 2022-02-22T18:33:06.536Z
tags: react, web-framework
editor: markdown
---

# Render and Commit Phases
React will start at the root of the component tree and recursively loop downwards, finding all components that have been flagged as needing updates. For each flagged component, React will call that component's render method. The render method will output how that particular component will look like in the DOM, given its props and state at the time of the render.

React will then do a diff of the new tree of objects (sometimes referred to as the "virtual DOM"). When doing this, React will collect a list of all changes that need to be applied to make the real DOM look like the current desired output.
 

