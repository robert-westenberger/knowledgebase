---
title: CSS Interview Questions
description: 
published: true
date: 2022-03-25T14:47:38.343Z
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
It's a CSS positional property. They can be floated to the left or right. The default is no float at all.
 
If all elements in a container are floated, its height will collapse to 0. This is corrected by a clearfix. 

**There is never a reason, under any circumstance to use floats anymore.**

# Describe `z-index` and how stacking context is formed
The `z-index` property controls vertical stacking order of elements that overlap. It only works on elements with a `position` property that is anything but `static`. 

Without any `z-index` value, they are stacked based off of where they appear in the DOM (lowest one down at the same hierarchy level appears on top). 

## Stacking Context
A stacking context is formed, anywhere in the document, by any of the following scenarios:

- Root element of the document (`<html>`).
- Element with a position value absolute or relative and z-index value other than auto.
- Element with a position value fixed or sticky (sticky for all mobile browsers, but not older desktop).
- Element that is a child of a flex container, with z-index value other than auto.
- Element that is a child of a grid container, with z-index value other than auto.
- Element with an opacity value less than 1 
- Element with a mix-blend-mode value other than normal.
- Element with any of the following properties with values other than `none`:
	- transform
  - filter
  - perspective
  - clip-path
  - mask / mask-image / mask-border

