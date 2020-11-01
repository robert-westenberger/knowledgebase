---
title: Lights
description: 
published: true
date: 2020-11-01T04:23:54.550Z
tags: webgl, web-technologies
editor: markdown
---

# Lights


### Positional vs Directional
Light sources can be positional or directional. Directional lighting is simpler and less computationally expensive than positional lighting.
* **Positional** - It's position will determine how a scene is lit. A lamp inside a room is a positional light source. Objects far away will receive little light and may be obscured. This is modeled by a point in space.
* **Directional** - Will illuminate all objects in a scene, regardless of distance from the source. The sun is an example of a directional light source. A directional light is modeled with a normalized vector that indicates its direction. 

### Normals
**Normals** are [vectors](/mathematics/linear-algebra/vectors-and-spaces) that are perpendicular to the surface we want to illuminate.They represent the orientation of the surface and are therefore critical to modeling the interaction between a light source and the object. 

### Material
**Materials** control how an object appears on the screen. It can be modeled by several params, including its color and texture. 

