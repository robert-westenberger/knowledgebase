---
title: Rendering
description: 
published: true
date: 2020-10-03T05:45:55.377Z
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