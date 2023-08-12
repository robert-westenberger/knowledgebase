---
title: Deep Learning
description: 
published: true
date: 2023-08-12T18:18:03.479Z
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
## Computer Vision 
### Object recognition
Computers can recognize what items are in an image at least as well as people can - even specially trained people like radiologists. 

### Object detection
Computers are also good at recognizing where objects in an image are, and can highlight their locations and name each found object.

### Downsides
Not good at recognizing images that are significantly different than the training set (e.g., training on photos and then giving the trained model a handdrawn image).

In production, we can check for **out-of-domain** data, which is data the model has not been trained on (in the example above, checking for handdrawn images when the model has been trained on photos).

### Data augmentation
Labelling data for object detection can be slow and expensive. One approach that is helpful is to synthetically generate variations of input images, such as by rotating them or changing their brightness and contrast. This is **data augmentation** and also works well for text and other types of models.

## Text (Natural Language Processing)
### Classifying Text
Computers are good at classifying both short and long documents based on whether it's spam or not spam, sentiment analysis, author, source website, etc.
### Generating text
Computers are good at generating context appropriate text, such as 
replies to social media posts, and imitating a particular author's style. 
### Downsides
Deep learning is currently not good at generating correct responses. We currently don't have a good way of combining a knowledge base of medical information with a deep learning model for generating medically correct natural language responses.