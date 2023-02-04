---
title: Drawing Multiple Things
description: 
published: true
date: 2023-02-04T21:08:59.742Z
tags: webgl
editor: markdown
---

# Typical Architecture for a WebGL Program

If you had a function that draws a circle, you could program it like this: 

```
function drawCircle(centerX, centerY, radius, color) { ... }
```


or like this

```

let centerX;
let centerY;
let radius;
let color;
 
function setCenter(x, y) {
   centerX = x;
   centerY = y;
}
 
function setRadius(r) {
   radius = r;
}
 
function setColor(c) {
   color = c;
}
 
function drawCircle() {
   ...
}

```