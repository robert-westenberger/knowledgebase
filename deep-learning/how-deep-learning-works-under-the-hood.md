---
title: How deep learning works under the hood
description: 
published: true
date: 2023-08-13T19:21:20.360Z
tags: deep-learning, machine-learning
editor: markdown
---

# Training a Digit Classifier
## Pixels: The Foundations of Computer Vision
In a computer, everything is represented as a number. To view the numbers that make up a particular image, we can convert it to a NumPy array or a PyTorch tensor. 

Here is an example using numpy

```
array(<open PIL image>)[4:10,4:10]
```

it outputs

```
array([[  0,   0,   0,   0,   0,   0],
       [  0,   0,   0,   0,   0,  29],
       [  0,   0,   0,  48, 166, 224],
       [  0,  93, 244, 249, 253, 187],
       [  0, 107, 253, 253, 230,  48],
       [  0,   3,  20,  20,  15,   0]], dtype=uint8)
```

The `4:10` indicatres we requested the rows from index 4 (inclusive) to 10 (not inclusive), same for cols. NumPy indexes from top to bottom and left to right, so this section is located in the top-left corner of the image.

The same thing in a PyTorch sensor: 

```
tensor(im3)[4:10,4:10]
```

```
tensor([[  0,   0,   0,   0,   0,   0],
        [  0,   0,   0,   0,   0,  29],
        [  0,   0,   0,  48, 166, 224],
        [  0,  93, 244, 249, 253, 187],
        [  0, 107, 253, 253, 230,  48],
        [  0,   3,  20,  20,  15,   0]], dtype=torch.uint8)
```

Below we use Pandas DataFrame to color-code the values using a gradient, which shows us clearly how the image is created from pixel vals: 

```
im3_t = tensor(im3)
df = pd.DataFrame(im3_t[4:15,4:22])
df.style.set_properties(**{'font-size':'6pt'}).background_gradient('Greys')
```

![pandas_dataframe.png](/pandas_dataframe.png)

We can see white pixels are stored as 0, black as 255, and shades of grey between both. 

## First try: Pixel Similarity
So we need to create a model that can recognize 3s and 7s. How about we find the average pixel value for every pixel of the 3s, then do the same for the 7s. That will give us two group averages, defining what we mgiht call the "ideal" 3 and 7. 