---
title: Rendering
description: 
published: true
date: 2020-10-04T06:28:01.505Z
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
* Definitions of VBOs and IBOs for a square.
```
// Set up the buffers for the square
function initBuffers() {
  /*
    V0                    V3
    (-0.5, 0.5, 0)        (0.5, 0.5, 0)
    X---------------------X
    |                     |
    |                     |
    |       (0, 0)        |
    |                     |
    |                     |
    X---------------------X
    V1                    V2
    (-0.5, -0.5, 0)       (0.5, -0.5, 0)
  */
  const vertices = [
    -0.5, 0.5, 0,
    -0.5, -0.5, 0,
    0.5, -0.5, 0,
    0.5, 0.5, 0
  ];

  // Indices defined in counter-clockwise order
  indices = [0, 1, 2, 0, 2, 3];

  // Setting up the VBO
  squareVertexBuffer = gl.createBuffer();
  gl.bindBuffer(gl.ARRAY_BUFFER, squareVertexBuffer);
  gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(vertices), 
   gl.STATIC_DRAW);

  // Setting up the IBO
  squareIndexBuffer = gl.createBuffer();
  gl.bindBuffer(gl.ELEMENT_ARRAY_BUFFER, squareIndexBuffer);
  gl.bufferData(gl.ELEMENT_ARRAY_BUFFER, new Uint16Array(indices), 
   gl.STATIC_DRAW);

  // Clean
  gl.bindBuffer(gl.ARRAY_BUFFER, null);
  gl.bindBuffer(gl.ELEMENT_ARRAY_BUFFER, null);
}
```
* For every buffer, we want to..
  * Create a new buffer
  * Bind it to make it the current buffer
  * Pass the buffer data using one of the typed arrays
  * Unbind the buffer
  
#### Associating Attributes to VBOs 
![associating_attributes_to_vbos.png](/associating_attributes_to_vbos.png)
1. Bind a VBO
2. Point an attribute to the currently-bound VBO
3. Enable the attribute
4. Unbind.
![pointing_attribute_to_currently_bound_vbo.png](/pointing_attribute_to_currently_bound_vbo.png)

## Rendering
Once VBOs have been defined and mapped to corresponding vertex shader attributes, we are ready to render. WebGL provides *drawArrays* sor *drawElements*, both writing to the framebuffer. Both will only use enabled arrays.
* drawarrays - uses vertex data in the order in which its defined in the buffer to create the geometry.
* drawelements - uses indices to access vertex data buffers to create the geometry. 

### Using drawArrays
drawArrays is used when the geometry is simple enough that defining indices is overkill.![drawarrays.png](/drawarrays.png)
