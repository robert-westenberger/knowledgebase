---
title: Section 3.3 Modeling with Mutable Data
description: 
published: true
date: 2021-01-10T03:10:16.459Z
tags: book-notes
editor: markdown
---

# Modeling with Mutable Data

In order to model compound objects with changing state, we will design data abstractions to include, in addition to selectors and constructors, operations called *mutators*, which modify data objects. Data objects that have mutators are *mutable data objects*. 

### Sharing and identity
Sharing is undetectable if data objects are not mutated. However if two different data objects contain members that point to the same piece of data in memory; mutating data for one object that points to a common object can cause unanticipated results. 


### Queues
[Queues](/computer-science/Queues)
We could represent a queue as a regular list, but this would require us to scan the entire list to find the end of the queue (since a list only providers a pointer to the beginning of the list and we have to tail our way down to the end of the list).

To avoid this drawback we can represent the queue as a list, together with an additional pointer that indicates the final pair in the list.



