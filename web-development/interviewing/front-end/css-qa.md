---
title: CSS Interview Questions
description: 
published: true
date: 2022-03-25T15:52:42.320Z
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
- Element with a `isolation` value `isolate`. 
- Element with a `contain` value of `layout`, or `paint`, or a composite value that includes either of them.

# Explain CSS Sprites, and how you would implement them on a page or site. 
Combines multiple images into one larger image. It's a commonly used technique for icons. Images are extracted from the larger sprite using `background-image`, `background-position`, and `backgorund-size` properties.

# How would you approach fixing browser-specific styling issues?
- After identifying the issue and the offending browser, use a separate style sheet that only loads when that specific browser is being used. This requires SSR though. 
- Use a library like bootstrap that already handles this for you.
- Use autoprefixer to automatically add vendor prefixes.
- Use reset CSS or normalize CSS.
- Many css transpilation libraries, like PostCSS, already handle this for you and will transform problematic sections of styles into corresponding safe code based off of targets you provide. 

# How do you serve your pages for feature-constrained browsers? 
## Graceful degradation
The practice of building an application for modern browsers while ensuring it remains functional in older browsers.
## Progressive enhancement
The practice of building an application for a base level of ux, but adding functional enhancements when a browser supports it. 
## Check for feature support
Use caniuse.com to check for feature support.
## Feature detection
Use something like modernizr to check for what features the user's browser supports.
Or on more modern browsers, the CSS @support query.

# What are different ways to visually hide content (and make it only available for screen readers?)
These techniques are related to accessibility (a11y).

- width: 0; height: 0. Make the element not take up any space on the screen at all, resulting in not showing it.
- position: absolute; left: -99999px. Position it outside of the screen.
- text-indent: -9999px. This only works on text within the block elements.
- Meta tags. For example by using Schema.org, RDF, and JSON-LD.
- WAI-ARIA. A W3C technical specification that specifies how to increase the accessibility of web pages.
Even if WAI-ARIA is the ideal solution, I would go with the absolute positioning approach, as it has the least caveats, works for most elements and it's an easy technique.

# What are some of the "gotchas" for writing efficient CSS?
## Avoid universal and tag key selectors
Browsers match selectors from rightmost to left. Browsers filter out elements in the DOM according to this rightmost (key) selector and traverse up its parent elements to determine matches. So, avoid key selectors that are tag and universal selectors.
## Be aware of CSS properties that trigger reflow, repaint, and compositing

# Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models
The CSS Box model is responsible for calculating:
- How much space a block element takes up
- Whether or not borders and/or margins overlap, or collapse
- A box's dimensions.

- The dimensions of a block element are calculated by width, height, padding, borders, and margins.
- If no height is specified, a block element will be as high as the content it contains, plus padding (unless there are floats, for which see below).
- If no width is specified, a non-floated block element will expand to fit the width of its parent minus padding.
- The height of an element is calculated by the content's height.
- The width of an element is calculated by the content's width.
- By default, paddings and borders are not part of the width and height of an element.

# Compare `block`, `inline`, and `inline-block`
|  | block | inline-block | inline |
|---|---|---|---|
| size | fills up width of its parent container | depends on content | depends on content |
| Positioning | start on a new line and  tolerates no HMTL elements next to it (except for floats | flows along with other content and allows other elements beside it | flows along with other content and allows other elements beside it |
| Can specify width  and height | yes | yes | no, will ignore it |
| Can be aligned with  vertical-align | no | yes | yes |
| margins and paddings | all sides respected | all sides respected | only horizontal respected. Vertical sides  dont affect layout. Vertical space it takes up  depends on line-height, even though the border and padding appear visually around the content. |
| float | - | - | Becomes like a block element where you  can set vertical margins and paddings. |

# What's the difference between a `relative`, `fixed`, `absolute`, and `static`ally positioned element?