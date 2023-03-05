---
title: MipMaps
description: 
published: true
date: 2023-03-05T22:46:44.625Z
tags: webgl
editor: markdown
---

# What are Mipmaps
Mipmaps are pre-calculated, optimized sequences of images, each of which is a progressively lower resolution representation of the previous.

You can visualize mipmaps as a pyramid of images. The base of the pyramid is the full sized image in the original resolution. As you ascend up the pyramid, each level is a progressively lower resolution.

# What are they used for?
They are intended to increase rendering speed and reduce aliasing artifacts. A high-resolution mipmap image is used for high-density samples, such as for objects close to the camera; lower-resolution images are used as the object appears farther away.