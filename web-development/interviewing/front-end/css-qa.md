---
title: CSS Interview Questions
description: 
published: true
date: 2022-03-25T14:39:12.110Z
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

The resulting matrix of values are compared column by column. When comparing selectors to determine which has the highest specificity, look from left to right, and compare the highest value in each column. So a value in column `b` will override values in columns `c` and `d`, no matter what they might be. 

In the case of equal specificity, the last rule declared is applied. 

# What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?

- **Resetting** - Strips all default browser styling on elements. You'll have to redeclare styling for common typographic elements.

- **Normalizing** - Preserves useful default styles rather than unstyling everything. It also corrects bugs for common browser dependencies.

Resetting is a good choice for a highly customized or unconventional website.

# Describe `float`s and how they work
It's a CSS 