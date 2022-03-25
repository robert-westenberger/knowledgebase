---
title: CSS Interview Questions
description: 
published: true
date: 2022-03-25T14:34:10.018Z
tags: interviewing, css, front-end
editor: markdown
---

# What is CSS Selector Specifity and how does it work?
When multiple CSS rules, of the same rule, are applied to a particular element, the browser calculates which one is actually applied based off of the following algorithm:

Four comma-separated values, `a,b,c,d` are calculated based off the following:

`a`: Whether inline styles are being used. 1 if its inline, 0 if not.

`b`: number of ID selectors

`c`: number of classes, attributes and pseudo-classes selectors

`d`: number of tags and pseudo-element selectors.


