---
title: Notes
description: 
published: true
date: 2023-01-29T18:53:45.771Z
tags: webgl, 3d-graphics
editor: markdown
---

From http://learnwebgl.brown37.net/index.html


WebGL is mainly comprised of
- An HTML canvas element in the web page provides a rectangular area inwhich 3D graphics can be rendered.
- Graphical data that defines the 3D objects to be rendered
- Javascript to load / configure / render graphical data and code that responds to user events.
- OpenGL Shader programs that perform critical parts of the graphical rendering.


GPU's are specially designed to render 3D graphics. Also, graphics memory is a separate memory system for video and graphics processing. 

When data is to be rendered, it is placed into the GPU's memory. This typically only happens once in a typical graphics program. Once some data is in the GPU's memory, it can be rendered very quickly and efficiently. 

In general, expensive operations are only done once. This is the **preprocessing step**. The **rendering step** happens many times and is the part that is performed each time an object is drawn.


![data_location.png](/data_location.png)
Above is where the different parts of a WebGL program are stored and executed.


# The Graphics Pipeline
## Input model data
Feed data into the pipeline, including model vertices (x,y,z) that define location, normal vectors (dx,dy,dz) that define direction, and color data.

# File Organization for WebGL Programs
- An HTML file which contains the web page description.
- One or more CSS files which describe the properties of the HTML elements on the web page.
- One or more JavaScript files which provide the processing logic for the WebGL program.
- One or more data files which describe the objects that will be rendered.
- One or more shader files which are the rendering programs for the graphics pipeline.
