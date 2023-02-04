---
title: Drawing Multiple Things
description: 
published: true
date: 2023-02-04T21:12:30.710Z
tags: webgl
editor: markdown
---

# Architecture of WebGL

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

WebGL works the second way.

Functions like `gl.createBuffer`, `gl.bufferData`, `gl.createTexture`, and `gl.texImage2D` let you upload buffer (vertex) and texture (color, etc..) data to WebGL. `gl.createProgram`, `gl.createShader`, `gl.compileShader`, and `gl.linkProgram` let you create your GLSL shaders. Nearly all the rest of the functions of WebGL are setting up these global variables or state that is used when `gl.drawArrays` or `gl.drawElements` is finally called.

# Typical Structure
## Init Time