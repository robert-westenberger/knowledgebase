---
title: How deep learning works under the hood
description: 
published: true
date: 2023-08-13T20:55:47.615Z
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
So we need to create a model that can recognize 3s and 7s. How about we find the average pixel value for every pixel of the 3s, then do the same for the 7s. That will give us two group averages, defining what we mgiht call the "ideal" 3 and 7. Then, to classify the image as one diit or the other, we see which of these two ideal digits the image is most similar to. 

This will make a good **baseline** ( a simple model which you are confident should perform reasonably well. It should be simple to test and implement, so we can use it to compare to more complex models).


### Get average of pixel values 
First, we get the average of the pixel values for each of our two groups.

We create a tensor containing all of the 3s stacked together, and a tensor for all the 7s stacked together. We used python list comprehensions to create a plain list of the single image tensors.

```
seven_tensors = [tensor(Image.open(o)) for o in sevens]
three_tensors = [tensor(Image.open(o)) for o in threes]
```

We use fastai's `show_image` function to display the tensors.

```
show_image(three_tensors[1])
```

will show an image of a "3".

For every pixel position, we want to compute the average over all the images of the intensity of that pixel. We first combine all the images into a single 3D tensor. This is commonly referred to a `rank-3 tensor`. We often need to stack up individual tensors in a collection into a single tensor.

Some operations in PyTorch, like taking a mean, require us to cast our integer types to float types. Casting in PyTorch is as simple as typing the name of the type you wish to cast to, and treating it as a method.

Generally when images are floats, the pixel values ar eexpected to be between 0 and 1, and so we will divide by 255 here:

```
stacked_sevens = torch.stack(seven_tensors).float()/255
stacked_threes = torch.stack(three_tensors).float()/255
stacked_threes.shape
```

The most important thing about a tensor is it's `shape`, which is the length of each axis. The above outputs

```
torch.Size([6131, 28, 28])
```

we can see we have 6131 images, each 28x28 pixels.

The **length** of a tensor's shape is it's rank (in other words, it's just it's  number of axes / dimensions.

```
len(stacked_threes.shape)
```

Now, we calculate the mean of all the image tensors by taking the mean along dimension 0 of our stacked, rank-3 tensor. This is the dimension that indexes over all the images. 

In other words, for every pixel position, this will compute the average of that pixel over all images. The result will be one value for every pixel position, or a single image. 

```
mean3 = stacked_threes.mean(0)
show_image(mean3);
```
