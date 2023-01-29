---
title: Shaders
description: 
published: true
date: 2023-01-29T23:57:30.765Z
tags: webgl
editor: markdown
---

# Shaders
## Vertex Shader
A Vertex Shader's job is to generate clip space coordinates. It always takes the form
```
void main() {
   gl_Position = doMathToMakeClipspaceCoordinates
}
```

Your shader is called once per vertex. Each time it's called you are required to set the special global variable, `gl_Position` to some clip space coordinates.


### Ways vertex shaders get data

#### Attributes
Data pulled from buffers.
#### Uniforms
Values that stay the same for all vertices of a single draw call.
#### Textures
Data from pixels/texels