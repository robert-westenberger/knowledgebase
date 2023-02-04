---
title: Drawing Multiple Things
description: 
published: true
date: 2023-02-04T21:19:17.039Z
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
- create all shaders and programs and look up locations
- create buffers and upload vertex data
- create textures and upload texture data

## Render Time
- clear and set the viewport and other global state (enable depth testing, turn on culling, etc..)
- For each thing you want to draw
	- call `gl.useProgram` for the program needed to draw.
  - setup attributes for the thing you want to draw
  	- for each attribute call `gl.bindBuffer`, `gl.vertexAttribPointer`, `gl.enableVertexAttribArray`
  - setup uniforms for the thing you want to draw
  	- call `gl.uniformXXX` for each uniform
    - call `gl.activeTexture` and `gl.bindTexture` to assign textures to texture units. 
  - call `gl.drawArrays` or `gl.drawElements`
  

