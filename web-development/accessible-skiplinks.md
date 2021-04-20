---
title: Accessible Skiplinks
description: 
published: true
date: 2021-04-20T02:57:23.751Z
tags: accessibility, html
editor: markdown
---

# Accessible Skiplinks
Should always be at the very top of the page, right after the opening body tag

## Visible Links
Highly accessible but may be intrusive to visual design. The link is presented to all users, even sighted mouse users who may not use it, or that could potentially be confused by it.
## Invisible Links
It is a strict requirement for skip links that they be **visible on keyboard focus**. 

One potential issue is if the user tabs very quickly, the skip link is focused and visually noticeable for a fraction of a second. CSS transitions can be used to cause the link to animate so it remains visible on the screen for a period of time. 