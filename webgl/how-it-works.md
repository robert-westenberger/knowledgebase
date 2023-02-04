---
title: How It Works
description: 
published: true
date: 2023-02-04T21:24:17.211Z
tags: webgl
editor: markdown
---

# Interaction between WebGL and the GPU

Basically 2 parts. 

The first part processes vertices (or streams of data) into clip space vertices. 

Second part draws pixels based on the first part.


When you call 
```
const primitiveType = gl.TRIANGLES;
const offset = 0;
const count = 9;
gl.drawArrays(primitiveType, offset, count);
```

The `9` means "process 9 vertices" so here are 9 vertices being processed.


![vertex-shader-anim.gif](/vertex-shader-anim.gif)

On the left is the data you provide. The vertex shader is a function you write in GLSL.