---
title: How deep learning works under the hood
description: 
published: true
date: 2023-09-04T15:43:49.275Z
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
![averaged_3.png](/averaged_3.png)

### Measure the difference from an arbitrary 3 and the ideal 3
There are two main ways data scientists measure distance in this context:

- Take the mean of the absolute value of differences. This is the **mean absolute difference** or **L1 norm**.
- Take the mean of the square of differences ( which makes everything positive) and then take the square root (which undoes the squaring). This is called the **root mean squared error (RMSE)** or **L2 norm**.


Now we try both of these:

```
dist_3_abs = (a_3 - mean3).abs().mean()
dist_3_sqr = ((a_3 - mean3)**2).mean().sqrt()
dist_3_abs,dist_3_sqr
```
which outputs 
`(tensor(0.1114), tensor(0.2021))`

and
```
dist_7_abs = (a_3 - mean7).abs().mean()
dist_7_sqr = ((a_3 - mean7)**2).mean().sqrt()
dist_7_abs,dist_7_sqr
```
which outputs
`(tensor(0.1586), tensor(0.3021))`

We can see the distance between the arbitrarily chosen 3 and the "ideal" 3 is less than the distance to the ideal 7. So our simple model gives the right prediction in this case.

PyTorch provides both of these as loss functions, which the PyTorch team recommends importing as `F` (and is available by default under that name in fastai).

```
F.l1_loss(a_3.float(),mean7), F.mse_loss(a_3,mean7).sqrt()
## (tensor(0.1586), tensor(0.3021))
```

Here, `mse` stands for mean squared error, and `l1` referes to the standard mathematical jargon for mean absolute value (the L1 norm).

### NumPy Arrays and PyTorch Tensors
We generally use PyTorch tensors over NumPy arrays because PyTorch tensors are GPU accelerated, which are critical for deep learning.

NumPy and PyTorch are both wrappers around compiled objects written and optimized in another language, like C, since python is so slow.

A NumPy array is a multidimensional table of data, which can be any type at all. The innermost arrays can potentially be different sizes - this is a "jagged array". If all the items are all of some simple type like integer or float, then NumPy will store them as a compact C data structure in memory.

A PyTorch tensor is nearly the same thing as a NumPy array, but with additional restrictions that unlocks some additional capabilities. A PyTorch tensor must use a single basic numeric type for all components. It can't be jagged like a NumPy array can. It's always a regularly shaped multidimensional rectangular structure.

One major capability PyTorch has over NumPy is that PyTorch's structures can live on the GPU and run much faster. In addition, PyTorch can automatically calculate derivatives of these operations, including combinations of operations. 

#### Creating arrays or tensors
```
data = [[1,2,3],[4,5,6]]
arr = array (data)
tns = tensor(data)
```

#### Accessing tensors
This will select the second row
```
tns[1]
## tensor([4,5,6])
```

Selecting a column, we use `:` to indicate all of the first axis:

```
tns[:,1]
## tensor([2,5])
```

You can combine these with python slice syntax (`[start:end]`, with `end` being non inclusive) to select part of a row or column
```
tns[1,1:3]
## tensor([5,6])
```

#### Manipulating tensors
You can use the standard operations `+`, `-`, `*`, `/`
```
tns+1
```
will output
```
tensor([[2, 3, 4],
        [5, 6, 7]])
```

tensors have a type
`tns.type()` here will output `torch.LongTensor`. It automatically changes.

if we assign a value to `tns*1.5`, it will be a tensor, but this type of type `torch.FloatTensor`.


## Computing Metrics Using Broadcasting
Now we have a baseline model, but is it any good?

Recall that a metric is a number calculated based on the predictions of our model, and the correct labels in our dataset, in order to tell us how good our model is. 

We want to calculate our metric over a validation set, so we don't inadvertently train our model to work well only on training data (overfitting). This isn't really necessary because with the pixel similarity model, it has no trained components, but it's a good habit we do this anyway.

Let's create tensors from our `3s` and `7s` directory. These are the tensors we will use to calculate a metric measuring the quality of our first-try model, which measures the distance from an ideal image:

```
valid_3_tens = torch.stack([tensor(Image.open(o)) 
                            for o in (path/'valid'/'3').ls()])
valid_3_tens = valid_3_tens.float()/255
valid_7_tens = torch.stack([tensor(Image.open(o)) 
                            for o in (path/'valid'/'7').ls()])
valid_7_tens = valid_7_tens.float()/255
valid_3_tens.shape,valid_7_tens.shape
## (torch.Size([1010, 28, 28]), torch.Size([1028, 28, 28])) <-- the shape of each tensor
```

We ultimately want a function, `is_3`, that will decide if an arbitrary image is a 3 or a 7, based on which of the two "ideal digits" the arbitrary image is closer to. 

We can write a simple function that calculates the mean absolute error:

```
def mnist_distance(a,b): return (a-b).abs().mean((-1,-2))
mnist_distance(a_3, mean3)
## tensor(0.1114)
```

Note that passing (-1,-2) to the mean function means we are computing the average across the last two dimensions of the tensor (ours is (batch_size, width, height)). 


In order to calculate a metric for overall accuracy, we need to calculate the distance to the ideal 3 for every image in the validation set. We could write a loop over all the single image tensors that are stacked within our validationset tensor, but there is a better way. 

We can pass in the tensor representing the 3s validation set to our function:

```
valid_3_dist = mnist_distance(valid_3_tens, mean3)
valid_3_dist, valid_3_dist.shape
## (tensor([0.1050, 0.1526, 0.1186,  ..., 0.1122, 0.1170, 0.1086]),
 torch.Size([1010]))
```
Instead of complaining about shapes not matching, it returned the distance for every single image as a vector (a rank-1 tensor) of length 1010 (the number of 3s in our validation set). 

This happened because PyTorch used **broadcasting**. When PyTorch tries to perform a simple subtraction operation between two tensors of different ranks, it will automatically expand the tensor with the smaller rank to ahve the same size as the one with the larger rank. 

After broadcasting so the two argument tensors have the same rank, PyTorch applies its usual logic for two tensors of the same rank: it performs the operation on each corresponding element of the two tensors, an returns the tensor result.

For instance,

```
tensor([1,2,3]) + tensor(1)
## tensor([2,3,4])
```
In this case, PyTorch treats `mean3`, a rank-2 tensor representing a single image, as if it were 1010 copies of the same image, and then subtracts each of those copies from each 3 in our validation set.

```
valid_3_tens.shape
## torch.Size([1010, 28, 28])

mean3.shape
## torch.Size([28, 28])

(valid_3_tens-mean3).shape
## torch.Size([1010, 28, 28])
```

We can use `mnist_distance`, defined above, to figure out whether an image is a 3 or not by using the following logic: if the distance between the digit in question and the ideal 3 is less than the distance to the ideal 7, then it's a 3. This function will automatically do broadcasting and be applied elementwise, just like all PyTorch functions and operators: 

```
def is_3(x): return mnist_distance(x,mean3) < mnist_distance(x,mean7)
```

We can test it on the full validation set of 3s thanks to broadcasting:

```
is_3(valid_3_tens)
## tensor([True, True, True,  ..., True, True, True])
```

Nowe we can calculate the accuracy for each of the 3s and 7s by taking the average of that function for all 3s and its inverse for all 7s.

```
accuracy_3s =      is_3(valid_3_tens).float() .mean()
accuracy_7s = (1 - is_3(valid_7_tens).float()).mean()

accuracy_3s,accuracy_7s,(accuracy_3s+accuracy_7s)/2
## (tensor(0.9168), tensor(0.9854), tensor(0.9511))
```

We can see we have over 90% accuracy on 3s, over 98% accuracy on 7s, and about 95% accuracy on both.
### Important broadcasting implementation details
PyTorch doesn't actually copy, in the above example `mean3`, 1010 times. It pretends if it were a tensor of that shape, but doesn't allocate any additional memory.

It does the whole calculation in C (or if you're using an nvidia GPU, in CUDA).

## Second try: Stochastic Gradient Descent (SGD)
We can't really improve our pixel similarity approach. We don;t have any kind of weight assignment, or any way of improving based on testing and effectiveness of a weight assignment. In other words, we can't really improve our pixel similarity approach by modifying a set of weights / paramters.

Instead of trying to find the similarity betwween an image and an "ideal image", we could instead look at each individual pixel and come up with a set of weights for each one, such that the highest weights are associated with those pixels most likely to be black for a particular category.

For instance, piels towards the bottom right are not very likely to be active for a 7, so they should have a low weight for a 7, but they are likely to be activated for an 8, so they should have a high weight for an 8. This can be represented as a function and set of weight values for each possible category - for instance the probability of being the number 8:

```
def pr_eight(x,w): return (x*w).sum()
```

Here we assume that `x` is the image, represented as a vector ( all the rows stacked up end to end in a single long line). The weights are a vector `w`. We just need a way to update the weights to make them a little better. We can repeat this step repeatedly until they are as good as we can make them.

We want to find the specific values for the vector `w` s.t. the result of our funciton will be high for those images that are actually 8s, and low for those images that are not. Searching for the best vector `w` is a way to search for the best function for recognising 8's.

Here are the steps we are going to require, to turn this function into a machine learning classifier: 

1. Initialize the weights. We initialize to random values.
2. For each image, use the weights to predict whether it appears to be a 3 or a 7. 
3. Based on these predictions, calculate how good the model is (its loss). The standard approach is to treat a small loss as good, and a large loss as bad.
4. Calculate the gradient, which measures for each weight, how changing that weight would change the loss.
5. Step (that is, change) all the weights based on that calculation.
6. Go back to step 2, repeating the process.
7. Iterate until you decide to stop the training process ( because the model is good enough or you don't want to wait any longer).

A simple way to figure out whether a weight should be increased by a bit or decreased by a bit would be to just try it: increase or decrease and see if the loss goes up or down. This process is a bit slow though. Calculus allows us to directly figure out in which direction, and by roughly how much, to change each weight, without having to try all these changes.

### Simple application of a loss function
Let's pretend the quadratic equation is our loss function.
```
def f(x): return x**2
```

![quadratic.png](/quadratic.png)


The sequence of steps we described earlier starts by picking some random value for a param, and calculating the value of the loss.

```
plot_function(f, 'x', 'x**2')
plt.scatter(-1.5, f(-1.5), color='red');
```
![loss1.png](/loss1.png)

Now we look to see what would happen if we increased or decreased our parameter by a little bit - the adjustment. This is just the slope at a particular point. 

![loss2.png](/loss2.png)

We can change our weight by a little in the direction of the slope, calculate our loss and adjustment again, and repeat this a few times. Eventually, we will get to the lowest point on the curve.

![loss3.png](/loss3.png)

The basic idea goes all the way back to Isaac Newton, who pointed out we can optimize arbitrary functions in this way. Regardless of how complicated our functions become, this basic approach of gradient descent will not significantly change. 


### Calculating Gradients
Recall that the [**derivative**](/mathematics/calculus/derivatives)of a function tells you how much a change in its parameters will change its result.

When we are calculating the derivatives for loss functions, the derivative with respect to a particular parameter tells us how the loss changes if you change that parameter slightly. When we know how changing a weight changes the value of the loss function, we know what we need to do in order to make it smaller.

Our function has lots of weights we need to adjust, so when we calculate the derivative we won't get back one number, but lots of them - a gradient for every weight. There isn't anything mathematically tricky here, you can calculate the derivative with respect to one weight, and treat all the other weights as constant, then repeat that for each weight. 

#### In PyTorch
```
xt = tensor(3.).requires_grad_()
```
The `requires_grad_` method tells PyTorch that we want to calculate gradients with respect to the variable at that value. 

```
yt = f(xt)
yt
## tensor(9., grad_fn=<PowBackward0>)
```

(recall that our function `f` is `f(x) x**2`. Notice how PyTorch prints not just the value calculated, but a note that it has a gradient function it'll be using to calculate our gradients when needed.

Finally, we tell PyTorch to calculate the gradients for us:
```
yt.backward()
```

The "backward" here refers to backpropagation, which is the name given to the process of calculating the derivative of each layer.
This is called the "backward pass" of the network, as opposed to the "forward pass", which is where the activations are calculated. 

We can now view the gradients by checking the grad attribute of our tensor. 

```
xt.grad
## tensor(6.)
```

Recall the derivative of $x^2$ is $2x$, and we have $x=3$, so the gradient should be $2*3=6$, which is what PyTorch calculated.

```
xt = tensor([3.,4.,10.]).requires_grad_()
xt
### tensor([ 3.,  4., 10.], requires_grad=True)
```

(Note that those are floats)

Now we'll add sum to our function so it can take a vector (a rank-1 tensor) and return a scalar (a rank 0 tensor)

```
def f(x): return (x**2).sum()

yt = f(xt)
yt
## tensor(125., grad_fn=<SumBackward0>)
```

Our gradients are `2*xt`, as we'd expect.

```
yt.backward()
xt.grad
## tensor([ 6.,  8., 20.])
```

The gradients only tell us the slope of our function, they don't actually tell us exactly how far to adjust the parameters. It gives us some idea of how far; if the slope is very large, then that may suggest we have more adjustments to do; if the slope is very small, that may suggest we are close to the optimal value.

### Stepping With a Learning Rate

Deciding how to change our parameters based on the values of the gradients is an important part of deep learning. Nearly all approaches start with the basic idea of multiplying the gradient by some small number, called the **learning rate (LR)**. It's often a number between 0.001 and 0.1.

Once you pick a learning rate, you can adjust your parameters using this simple function:

```
w -= gradient(w) * lr
```

This is stepping your parameters, using an optimizer step. Notice how we subtract `gradient * lr` from the parameter to update it. This allows us to adjust the parameter in the direction of the slope by increasing the parameter when the slope is negative and decreasing the parameter when the slope is positive. We want to adjust our parameters in the direction of the slope because our goal in deep learning is to minimize the loss.

The below image shows if we pick a learning rate that is too low, we don't get to the bottom of the slope without a lot of steps.

![low_learning_rate_descent.png](/low_learning_rate_descent.png)

This next image shows picking a learning rate that's too high. We can see the loss is actually getting worse. 
![high_learning_rate_descent.png](/high_learning_rate_descent.png)

This below image shows that when the learning rate is too high, it may "bounce" around rather than diverging.
![high_learning_rate_descent2.png](/high_learning_rate_descent2.png)


### An end-to-end SGD example
Now let's look at an example of how finding a minimum can be used to train a model to fit data better.

Imagine you were measuring the speed of a roller coaster as it went over the top of a hump. It would start fast, and then get slower as it went up the hill; it would be slowest at the top of the hill, and then it would speed up again as it went downhill. We want to build a model of how the speed changes over time. If we were measuring the speed manually every second for 20 seconds, it might look something like this:

```
time = torch.arange(0,20).float(); time
```

```
speed = torch.randn(20)*3 + 0.75*(time-9.5)**2 + 1
plt.scatter(time,speed);
```

![sgd_scatter_1.png](/sgd_scatter_1.png)

We've added a bit of random noise, since measuring things manually isn't precise. This means its not that easy to answer the question: What was the roller coaster's speed? Using SGD we can try to find a function that matches our observations. We can't consider every possible fn, so let's use a guess that it will be quadratic - a function of the form `a*(time**2)+(b*time)+c` .


We want to distinguish clearly between the function's input (the time when we are measuring the coaster's speed) and its parameters (the values that define which quadratic we're trying). So let's collect the parameters in one argument and thus separate the input, `t`, and the aprameters, `params`, in the functions signature: 

```
def f(t, params):
    a,b,c = params
    return a*(t**2) + (b*t) + c
```
In other words, we've restricted the problem of finding the best imaginable function that fits the data, to finding the best quadratic function. This greatly simplifies the problem, since every quadratic function is fully defined by the three parameters `a`, `b`, and `c`. To find the best quadratic function, we only need to find the best values for `a`, `b`, and `c`.

If we can solve this problem for the three params of a quadratic function, we'll be able to apply the same approach for other, more complex functions with more params - such as a neural net. Let's find the `f` first, and then we'll come back and do the same thing for the MNIST dataset with a neural net.

We need to define first what we mean by "best". We define this precisely by choosing a **loss function**, which will return a value vased on a prediciton and a target, where lower values of the function correspond to "better" predictions. It's important for loss functions to return lower values when predictions are more accurate, as SGD procedure we defined earlier will try to minimize this loss. For continuous data, it's common to use mean squared error:

```
def mse(preds, targets): return ((preds-targets)**2).mean()
```

#### Step 1: Initialize the parameters
First, we init the params to random vals, and tell PyTorch that we want to track their gradients, using `requires_grad_`

```
params = torch.randn(3).requires_grad_()
orig_params = params.clone()
```

#### Step 2: Calculate the predictions
Next, we calculate the predictions:
```
preds = f(time, params)
```

Let's create a little function to see how close our predictions are to our targets, and take a look.

```
def show_preds(preds, ax=None):
    if ax is None: ax=plt.subplots()[1]
    ax.scatter(time, speed)
    ax.scatter(time, to_np(preds), color='red')
    ax.set_ylim(-300,100)
```

![sgd_predict_1.png](/sgd_predict_1.png)

This doesn't look very close.

#### Step 3: Calculate the loss
```
loss = mse(preds, speed)
loss
## tensor(25823.8086, grad_fn=<MeanBackward0>)
```
Our goal is to improve this. To do this, we'll need to know the gradients.

#### Step 4: Calculate the gradients
The next steps is to calculate the gradients. In other words, calcualte an approximation of how the parameters need to change:

```
loss.backward()
params.grad
## tensor([82025.9219,  5272.2275,   342.7042])
```

```
params.grad * 1e-5
## tensor([0.8203, 0.0527, 0.0034])
```

We can use these gradients to improve our parameters. We'll need to pick a learning rate, for now let's use 0.00001 . 

```
params 
## tensor([ 1.5980,  0.1115, -0.0392], requires_grad=True)
```

#### Step 5: Step the weights
Now we need to update the params based on the gradients we just calculated:

```
lr = 1e-5
params.data -= lr * params.grad.data
params.grad = None
```

Understanding this bit depends on remembering recent history. To calculate the gradients we call `backward` on the `loss`. But this `loss` was itself calculated by `mse`, which in turn took `preds` as an input, which was calculated using `f` taking as an input `params`, which was the object on which we originally called `requires_grad_`—which is the original call that now allows us to call `backward` on `loss`. This chain of function calls represents the mathematical composition of functions, which enables PyTorch to use calculus's chain rule under the hood to calculate these gradients.

Let's see if the loss has improved:

```
preds = f(time,params)
mse(preds, speed)
## tensor(5435.5356, grad_fn=<MeanBackward0>)
```

and take a look at the plot again

```
show_preds(preds)
```

![preds.png](/preds.png)

We need to repeat this a few times, so we'll create a function to apply one step:

```
def apply_step(params, prn=True):
    preds = f(time, params)
    loss = mse(preds, speed)
    loss.backward()
    params.data -= lr * params.grad.data
    params.grad = None
    if prn: print(loss.item())
    return preds
```

#### Step 6: Repeat the process
Now we iterate. By looping and performing many improvements, we hope to reach a good result:

```
for i in range(10): apply_step(params)

## 5435.53564453125
## 1577.44921875
## 847.3778076171875
## 709.2225341796875
## 683.0758056640625
## 678.1243896484375
## 677.1838989257812
## 677.0023803710938
## 676.9645385742188
## 676.9537353515625
```
```
params = orig_params.detach().requires_grad_()
```

The loss is going down, just as we'd hoped. But looking only at these loss numbers disguises the fact that each iteration represents an entirely different quadratic funciton being tried, on the way to finding the best possible quadratic function.

We can see this process visually if we plot the function at every step. We can see how the shape is approaching the best possible quadratic function for our data:

```
_,axs = plt.subplots(1,4,figsize=(12,3))
for ax in axs: show_preds(apply_step(params, False), ax)
plt.tight_layout()
```

![sgd_iterations.png](/sgd_iterations.png)

#### Step 7: Stop
We just stopped at 10 epochs arbitrarily. In practice, we would watch the training and validation losses and our metrics to decide when to stop.

### Summarizing Gradient Descent
![gradient_descent.png](/gradient_descent.png)

To summarize, at the beginning the weights of our model can be random (training from scratch) or come from a pretrained model (transfer learning). The model will need to learn better weights.

We begin by comparing the outputs the model gives us with our targets ( we have labeled data, so we know what result the model should give us) using a loss function, which returns a number that we want to make as low as possible by improving our weights. To do this, we take a few data items from the training set and feed them to our model. We compare the corresponding targets using our loss function, and the score we get tells us how wrong our predictions were. We then change the weights a little bit to make it slightly better. 

To find how to change the weights to make the loss a bit better, we (well, PyTorch...) use calculus to calculate the gradients. 

#### An analogy for SGD
 Imagine you are lost in the mountains with your car parked at the lowest point. To find your way back to it, you might wander in a random direction, but that probably wouldn't help much. Since you know your vehicle is at the lowest point, you would be better off going downhill. By always taking a step in the direction of the steepest downward slope, you should eventually arrive at your destination. We use the magnitude of the gradient (i.e., the steepness of the slope) to tell us how big a step to take; specifically, we multiply the gradient by a number we choose called the learning rate to decide on the step size. We then iterate until we have reached the lowest point, which will be our parking lot, then we can stop.
 

## The MNIST Loss Function
We already have our independent variables `x` - the images themselves. We'll concatenate them all into a single tensor, and also change them from a list of matrices (a rank-3 tensor) to a list of vectors (a rank-2 tensor). We can do this using `view`, which is a PyTorch method that changes the shape of a tensor without changing its contents. `-1` is a special parameter to `view` that means "make this axis as big as necessary to fit all the data".

```
train_x = torch.cat([stacked_threes, stacked_sevens]).view(-1, 28*28)
```

We need a label for each image. We'll use `1` for 3s and `0` for 7s:

```
train_y = tensor([1]*len(threes) + [0]*len(sevens)).unsqueeze(1)
train_x.shape,train_y.shape
## (torch.Size([12396, 784]), torch.Size([12396, 1]))
```

A `Dataset` in PyTorch is required to return a tuple of `(x,y)` when indexed. Python provides a `zip` function which, when cominbed with `list`, provides a simple way to get this functionality:

```
dset = list(zip(train_x,train_y))
x,y = dset[0]
x.shape,y
## (torch.Size([784]), tensor([1]))
```

```
valid_x = torch.cat([valid_3_tens, valid_7_tens]).view(-1, 28*28)
valid_y = tensor([1]*len(valid_3_tens) + [0]*len(valid_7_tens)).unsqueeze(1)
valid_dset = list(zip(valid_x,valid_y))
```

Now we need an (initially random) weight for every pixel (this is the initialize step in our seven-step process).

```
def init_params(size, std=1.0): return (torch.randn(size)*std).requires_grad_()
```

```
weights = init_params((28*28,1))
```

The function `weights*pixels` won't be flexible enough-it is always equal to 0 when the pixels are equal to 0 (i.e. its intercept is 0). You might remember from high school math that the formula for a line is `y=w*x+b`; we still need the `b`. We'll initialize it to a random number too.

```
bias = init_params(1)
```

In neural networks, the `w` in the equation `y=w*x+b` is called the **weights**, and the `b` is called the **bias**. Together, the weights and bias make up the **parameters**.

We can now calculate a prediction for one image: 

```
(train_x[0]*weights.T).sum() + bias
## tensor([16.2561], grad_fn=<AddBackward0>)
```

While we could use a Python `for` loop to calculate the prediction for each image, that would be very slow (they don't run on the GPU). 

There's an extremely convenient mathematical operation that calculates the `w*x` for every row of a matrix - it's called matrix multiplication. 

![matrix_multiplication.png](/matrix_multiplication.png)

This image shows two matrices, `A` and `B`, being multiplied together. Each item of the result, which we'll call `AB`, contains each item of its corresponding row of `A` multiplied by each item of its corresponding column of `B`, added together. 

For instance, row 1, column 2 (the yellow dot with a red border) is calculated as 

$
a_{1,1} * b_{1,2}+a_{1,2} * b_{2,2}
$

In Python, matrix multiplication is represented with the `@` opreator. 

```
def linear1(xb): return xb@weights + bias
preds = linear1(train_x)
preds
## tensor([[16.2561],
##         [14.0191],
##         [16.8736],
##         ...,
##         [ 5.3612],
##         [ 5.3861],
##         [ 0.3403]], grad_fn=<AddBackward0>)
```

The first element is the same as we calculated before, as we expect. This equation, `batch@weights + bias`, is one of the two fundamental equations of any neural network (the other one is the activation function, which we'll see in a moment).

Let's check our accuracy. To decide if an output represents a 3 or a 7, we can just check whether its greater than 0.0, so our accuracy for each item can be calculated (using broadcasting, so no loops) with:

```
corrects = (preds>0.0).float() == train_y
corrects
## tensor([[ True],
##         [ True],
##         [ True],
##         ...,
##         [False],
##         [False],
##         [False]])
```

```
corrects.float().mean().item()
## 0.5855114459991455
```

Now let's see what the change in accuracy is for a small change in one of the weights (note that we have to ask PyTorch not to calculate the gradients as we do this, which is what `with torch.no_grad()` is doing here:

```
with torch.no_grad(): weights[0] *= 1.0001
```

```
preds = linear1(train_x)
((preds>0.0).float() == train_y).float().mean().item()
## 0.5855114459991455
```

As we've seen, we need gradients in order to improve our model using SGD, and in order to calculate the gradients we need some loss function that represents how good our model is. That is because the gradients are a measure of how that loss function changes with small tweaks to the weights.


So we need to choose a loss function. The obvious approach would be to use accuracy, which is our metric, as our loss function as well. We would calculate our prediction for each image, collect these values to calculate overall accuracy , and then calculate the gradients of each weight with respect to that overall accuracy.

Unfortunately, we have a significant technical problem here. The gradient of a function is its slope, or steepness, which can be defined as rise over run - how much the value of the function goes upo or down divided by how much we changed the input. 

We can write this mathematically as `(y_new - y_old) / (x_new - x_old)`. This gives us a good approximation of the gradient when `x_new` is very similar to `x_old`, meaning that their difference is very small. But accuracy only changes at all when a prediction changes from a 3 to a 7, or vice versa. The problem is that a small change in weights from `x_old` to `x_new` isn't likely to cause any prediciton to change, so `(y_new - y_old)` will almost always be 0. In other words, the gradient is 0 almost everywhere.

A very small change inthe value of a weight will often not actually change the accuracy at all. This means its not useful to use accuracy as a loss function - if we do, most of the time ourgradients will actually be 0, and the model will not be able to learn from that number. 

> In mathematical terms, accuracy is a function that is constant almost everywhere (except at the threshhold, 0.5), so its derivative is nil almost everywhere (and infinity at the threshhold). This then gives gradients that are 0 or infinite, which areuseless for updating the model.
{.is-info}

Instead, we need a loss function which, when our weights result in slightly better predictions, give us a slightly better loss. What does a "slightly better prediction" look like? In this case, it means that if the correct answer is 3 the score is a little higher, or if the correct answer is a 7 the score is a little lower.

Let's write such a function. What form does it take?

The loss function receives not the images themselves, but the predictions from the model. Let's make one argument, `prds`, of values between 0 and 1, where each value is the prediction that an image is a 3. It is a vector (rank-1 tensor), indexed over the images.

The purpose of the loss function is to measure the difference between predicted values and the true values - that is, targets (aka labels). Let's make another argument, `trgts`, with values of 0 or 1, which tells whether an image is actually a 3 or not. It is also a vector (rank 1 tensor), indexed over the images.

Suppose we had three images which we knew were a 3, 7, and a 3. Suppose our model predicted with high confidence (`0.9`) that the first was a 3, with slight confidence (`0.4`) that the second was a 7, and with fair confidence (`0.2`) but incorrectly that the last was a 7. That would mean our loss function would receive these values as inputs:

```
trgts  = tensor([1,0,1])
prds   = tensor([0.9, 0.4, 0.2])
```

Here's a first try at a loss function that measures the distance between `predictions` and `targets`:

```
def mnist_loss(predictions, targets):
    return torch.where(targets==1, 1-predictions, predictions).mean()
```

We're using a new function, `torch.where(a,b,c)`. This. is the same as running the list comprehension `[b[i] if a[i] else c[i] for i in range(len(a))]`, except it works on tensors, at C/CUDA speed. In plain English, this function will measure how distant each prediction is from 1 if it should be 1, and how distant it is from 0 if it should be 0, and then it will take the mean of all those distances.

Lets try it on our `prds` and `trgts`:

```
torch.where(trgts==1, 1-prds, prds)
## tensor([0.1000, 0.4000, 0.8000])
```

You can see that this function returns a lower number when predictions are more accurate, when accurate predicitons are more confident (higher absolute vals), and when inaccurate predictions are less confident). In PyTorch, we always assume that a lower values of a loss function is better. Since we need a scalar for the final loss, `mnist_loss` takes the mean of the previous tensor:

```
mnist_loss(prds, trgts)
## tensor(0.4333)
```

For instance, if we change our prediction for one of the "false" target from `0.2` to `0.8`,  the loss will go down, indicating that this is a better predictio:

```
mnist_loss(tensor([0.9, 0.4, 0.8]),trgts)
## tensor(0.2333)
```

One problem with the `mnist_loss` as currently defined is that it assumes that predictions are always between 0 and 1. We need to ensure then that this is actually the case.

### Sigmoid
The **sigmoid** function always outputs a number between 0 and 1. 

```
def sigmoid(x): return 1/(1+torch.exp(-x))
```

![sigmoid.png](/sigmoid.png)

It's a smooth curve that only goes up, which makes it easier for SGD to find meaningful gradients.

Let's update `mnist_loss` to first apply `sigmoid` to the inputs:

```
def mnist_loss(predictions, targets):
    predictions = predictions.sigmoid()
    return torch.where(targets==1, 1-predictions, predictions).mean()
```

### SGD and Mini-Batches
Now that we have a loss function that is driving SGD, we can consider some of the details involved in the next phase of the learning process, which is to change or update the weights based on the gradients. This is called the **optimization step**.

In order to take an optimization step we need to calculate the loss over one or more data items. We calculate the average loss for a few data items at a time (a mini-batch). We do this because calculating the loss for just one item would result in an imprecise and unstable gradient, and calculting it for the whole dataset would take too long.

The number of items in the mini-batch is called the **batch size**. A larger batch size means we'll get a more accurate and stable estimate of the dataset's gradients from the loss function, but it will take longer.


## Putting It All Together
Our process will be implemented something like this for each epoch:

```python
for x,y in dl:
    pred = model(x)
    loss = loss_func(pred, y)
    loss.backward()
    parameters -= parameters.grad * lr
```

First let's reinitialize our params

```
weights = init_params((28*28,1))
bias = init_params(1)
```

A DataLoader can be created from a Dataset

```
dl = DataLoader(dset, batch_size=256)
xb,yb = first(dl)
xb.shape,yb.shape
```

We can do the same for the validation set:

```
valid_dl = DataLoader(valid_dset, batch_size=256)
```

Let's create a mini-batch of size 4 for testing:
```
batch = train_x[:4]
batch.shape
## torch.Size([4, 784])
```

```
preds = linear1(batch)
preds 
## tensor([[-2.1876],
##         [-8.3973],
##         [ 2.5000],
##         [-4.9473]], grad_fn=<AddBackward0>)
```

```
loss = mnist_loss(preds, train_y[:4])
loss
## tensor(4.2580, grad_fn=<MeanBackward0>)
```

Now we can calculate the gradients:
```
loss.backward()
weights.grad.shape,weights.grad.mean(),bias.grad
## (torch.Size([784, 1]), tensor(-0.1511), tensor([-1.]))
```

Let's put all that in a function: 
```
def calc_grad(xb, yb, model):
    preds = model(xb)
    loss = mnist_loss(preds, yb)
    loss.backward()
```

and test it:
```
calc_grad(batch, train_y[:4], linear1)
weights.grad.mean(),bias.grad
## (tensor(-0.3022), tensor([-2.]))
```

But look at what happens if we call it twice:
```
calc_grad(batch, train_y[:4], linear1)
weights.grad.mean(),bias.grad
## (tensor(-0.6045), tensor([-4.]))
```

The gradients have changed. The reason is the `loss.backward` actually adds the gradients of `loss` to any gradients that are currently stored. So we have to set the current gradient to 0 first.

```
weights.grad.zero_()
bias.grad.zero_();
```