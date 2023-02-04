---
title: How It Works
description: 
published: true
date: 2023-02-04T21:23:16.174Z
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

![vertex-shader-anim.gif](/vertex-shader-anim.gif)