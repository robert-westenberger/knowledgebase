---
title: How It Works
description: 
published: true
date: 2023-02-04T23:11:02.026Z
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

Assuming you're drawing `TRIANGLES`, every time this first part generates 3 vertices the GPU uses them to make a tirnagle. It figures out which pixels the 3 points of the triangle correspond to, and then rasterizes the triangle which means "draws it with pixels".

For each pixel it will call your fragment shader asking what color to make that pixel. The fragment shader has to set an output color, used for that pixel.