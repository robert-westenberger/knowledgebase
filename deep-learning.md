---
title: Deep Learning
description: 
published: true
date: 2023-08-12T16:41:17.368Z
tags: ai, deep-learning, machine-learning, neural-networks
editor: markdown
---

# Overfitting
The longer you train for, the better your accuracy you will get on the training set. The validation set accuracy will also improve for a while, but eventually it will start getting worse as the model starts to memorize the training set, rather htan finding generalizable underlying patterns in the data.

![overfit.png](/overfit.png)

# What the Image Recognizer.. recognizes
Below layers are from a model called AlexNet.
## Layer 1
The first layer of an image recognition model recognizes very rudimentary and basic parts of an image. Horizontal, vertical, diagonal lines and gradients. These learned building blocks are very similar to the basic visual machinery of the human eye.
## Layer 2 