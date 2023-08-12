---
title: Deep Learning
description: 
published: true
date: 2023-08-12T18:08:06.889Z
tags: ai, deep-learning, machine-learning, neural-networks
editor: markdown
---

# Overfitting
The longer you train for, the better your accuracy you will get on the training set. The validation set accuracy will also improve for a while, but eventually it will start getting worse as the model starts to memorize the training set, rather htan finding generalizable underlying patterns in the data.

![overfit.png](/overfit.png)

# Image Recognition
## What the Image Recognizer.. recognizes
Below layers are from a model called AlexNet.
### Layer 1
The first layer of an image recognition model recognizes very rudimentary and basic parts of an image. Horizontal, vertical, diagonal lines and gradients. These learned building blocks are very similar to the basic visual machinery of the human eye.
### Layer 2 
At this layer, the model looks for corners, repeating lines, circles, and other simple patterns.
### Layer 3
The model recognizes and matches with higher level semantic components, like car wheels, text, flower petals.
### Layers 4
Even higher level semantic concepts, grouped by classification. Dog faces, bird's legs. 
### Layer 5
Entire objects with significant pose variation, e.g. keyboards, different breeds of dogs. 


## Fine tuning
When fine tuning an image recognition model, we adapt what those last layers focus on (flowers, humans, animals).

## Non-image tasks
You just need to convert data to images. 

### Interesting examples
- Sound can be converted to a spectrogram, which is a chart that shows the amount of each frequency at each time in an audio file.
- A binary file can be divided into 8-bit sequences that are convereted to decimal values. The decimal vector is reshaped and a gray-scale image is generated that represents the malware sample.
- Using mouse movement / heatmaps from users for fraud detection. 

# State of Deep Learning (as of 2020)
## Computer Vision (Object recognition)
Computers can recognize what items are in an image at least as well as people can - even specially trained people like radiologists. 