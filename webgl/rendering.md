---
title: Rendering
description: 
published: true
date: 2020-10-04T02:14:53.099Z
tags: 
editor: markdown
---

# WebGL
* WebGL uses immediate-mode rendering, as opposed to a declaritive retained-mode rendering. Retained-mode rendering holds the scene in memory, and the graphics library API can be called to update the scene. Immediate-mode rendering is procedural, requiring the application to update state itself and draw the scene from scratch each time. 

#### WebGL Application Elements
* Canvas element 
* Objects - 3D elements that make of the scene, rendered by WebGL using **buffers**.
* Lights - WebGL uses **shaders** to model lights in the scene. 
* Camera - Canvas element is the viewport into the 3D scene containing objects and lights. Different matrix operations are performed to produce a different perspective. 

#### WebGL Rendering Pipeline
* WebGL uses a **vertex shader** and **fragment shader** which runs on the GPU. The vertex shader computes values that can be used to rasterize geometric primitives (points, lines, triangles). The fragment shader computes a color for each pixel of the primitive being drawn. 

* **Vertex Buffer Objects** (VBOs) - contain vertex coordinates that is used to describe the geometry to be rendered in 3D space. 
* **Index Buffer Objects** (IBOs) - contain info about the relationship of vertices as rendering pipeline constructs the primitives.
* **Vertex shader** -  called on each VBO, manipulating coordinates, colors, texture coords.
* **Fragment Shader** - calculates the colors of individual pixels.
* **Framebuffer** - contains fragments that have been processed by the fragment shader.
* **Attributes** - Vertex attributes are used to communicate from "outside" to the vertex shader. Values are provided per vertex.
* **Uniforms** - Constants available to both the vertex and fragment shader during a rendering cycle. The position of a light is often modeled as a uniform.
* **Textures** - Arrays of data accessible by the shader program. 
* **Varyings** - Used to pass data from vertex to fragment shader.

#### Creating a simple geometric object in 3D space
* **Vertices** - floating point X,Y,Z coordinates of the points that define corners of 3D objects. WebGL requires vertices to be written in a JS array, which can be used to construct a WebGL buffer. 
* **Indices** - numeric labels for vertices in a given 3D scene.
![defining_geometry_webgl.png](/defining_geometry_webgl.png)

* WebGL uses Javascript Typed Arrays (Int16Array for IBOs since they are always integers, Float32Array for VBOs since vertexes can be floats) for buffer data.
* U 