---
title: Javascript Interview Questions
description: 
published: true
date: 2022-03-25T16:16:52.899Z
tags: interviewing, javascript
editor: markdown
---

# Event Delegation
A technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant element due to event bubbling up the DOM.

For example, instead of attaching an event indidvidually to each `<li>` in a list, you could attach it to just the `<ul>` and then check for the event target to see which list item was clicked.