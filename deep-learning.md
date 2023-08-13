---
title: Deep Learning
description: 
published: true
date: 2023-08-13T16:28:28.523Z
tags: ai, deep-learning, machine-learning, neural-networks
editor: markdown
---

# train_loss vs valid_loss vs error_rate
## train_loss
The loss function's value on the training dataset. It measures how well the model is fitting to the training data, but not necessarily how well it will generalize to unseen data.
## valid_loss
The loss function's value on the validation dataset. This dataset is not used during training. The validation loss gives an indication of how well the model is generalizing unseen data.
## error_rate
Metric that quantifies the number of mistakes the model makes. It could be calculated as the ratio of incorrect predictions to the total number of predictions. It is often used as a more interpretable measure of model performance.
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
### Translate text from one language to another
### Summarize long documents
### Find all mentions of a concept of interest
### Downsides
Deep learning is currently not good at generating correct responses. We currently don't have a good way of combining a knowledge base of medical information with a deep learning model for generating medically correct natural language responses.

## Combining text and images
A deep learning model can be trained on input images with output captions written in English, and can learn to generate surprisingly appropriate captions automatically for new images. There is no guarantee the captions will be correct, though.

## Tabular Data
Deep learning has recently been used as a part of an ensemble of multiple types of model (random forests, gradient boosting machines). Deep learning increases the variety of columns you can include - for example, columns containing natural language, and high-cardinality categorical columns (columns that contain a high number of discrete choices like zip code or product id).
## Recommendation Systems
Recommendation systems are really just a special type of tabular data. A company like Amazon represents every purchase as a giantsparse matrix, with customers as rows and products as columns. Data scientists apply some form of collaborative filtering to fill in the matrix.

For example, if customer A buys products 1 and 10, and customer B buys products 1, 2, 4, and 10, the engine will recommend that A buy 2 and 4.

### Downsides
Nearly all machine learning approaches only tell you what products a particular user might like, rather than what recommendations would be helpful for a user.

## Other data types
Often, domain-specific data types fit very nicely into existing categories. Protein chains look a lot like natural language documents, in that they are a long sequence of distinct tokens with complex relationships and meaning throughout the sequence. Using NLP is the current state-of-the-art approach for many types of protein analysis.

# The Drivetrain Approach
There are many accurate models that are useless, and many innacurate models that are highly useful. To ensure models are useful in practice, we need to consider how they will be used.


![drivetrain-approach.png](/drivetrain-approach.png)

Below are the steps, and we'll use the example of Google developing their first search engine.

## Defining a clear objective
Google considered, "What is the user's main objective when typing in a search query?". This lead them to their objective, which was to "show the most relevant search result". 

## Consider what levers can be pulled
What actions can we take to better achieve the objective? In Google's case, it's ranking of the search results.

## What new data can we collect?
What new data would Google need to produce such a ranking? They realized the implicit information regarding which pages linked to which other pages could be used for this purpose. 

## Use the above information to make a model
Our objective and available levers, what data we have and what additional data will need to be collected, determine what models can be built.

# Debugging model data
## Confusion Matrix
Below is a confusion matrix from a model that was tuned to identify black, grizzly, and teddy bears. We can see that the model had the best performance on teddy bears, guessing that one bear was teddy when in actuality it was a grizzly bear. 
![confusion_matrix.png](/confusion_matrix.png)

## Sorting data by loss
In the case of our model that is used to identify bears, we can sort images by their loss to see exactly where errors are occuring and determine whether it's due to a dataset problem (images aren't bears, the are labelled incorrectly, from a bad angle, etc).

Recall that loss is a number that is higher if the model is incorrect (especially if it's also confident of its incorrect answer), or if it's correct, but not confident of its correct answer. 

