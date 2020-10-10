---
title: Lights
description: 
published: true
date: 2020-10-10T04:15:22.371Z
tags: webgl, web-technologies
editor: markdown
---

# Lights


### Positional vs Directional
Light sources can be positional or directional.
* **Positional** - It's position will determine how a scene is lit. A lamp inside a room is a positional light source. Objects far away will receive little light and may be obscured. This is modeled by a point in space.
* **Directional** - Will illuminate all objects in a scene, regardless of distance from the source. The sun is an example of a directional light source. A directional light is modeled with a normalized vector that indicates its direction. 