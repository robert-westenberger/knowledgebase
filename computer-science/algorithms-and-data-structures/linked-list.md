---
title: Linked List
description: 
published: true
date: 2022-05-01T23:03:50.958Z
tags: data-structures, linked-lists
editor: markdown
---

# Advantages
- Elements are not continuous, so they are easy to expand. If you know the parent and child of a node, insertion or deletion can be done in constant time. 
- Overflow on linked structures never occurs unless the memory is actually full.
- Insertion and deletion are simpler than for static arrays. 
- With large records, moving pointers is easier and faster than moving the items themselves.
# Disadvantages
- Since storage space is not continuous, you can't calculate the address of corresponding elements according to an index, so you can't access it randomly. 
- Because each element must store a pointer to the location of it's parent and/or child nodes, it will consume more storage space. 