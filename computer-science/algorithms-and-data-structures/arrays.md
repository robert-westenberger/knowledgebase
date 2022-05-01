---
title: Arrays
description: 
published: true
date: 2022-05-01T22:44:06.033Z
tags: data-structures, arrays
editor: markdown
---

# Advantages
- Offer compact and continuous storage, which can be accessed randomly
- They make it possible to find elements quickly via index and use storage space efficiently.
# Disadvantages
- Because of the need for continuous chunks of memory, sufficient storage space must be allocated at one time. Therefore, if the array has to be expanded, we need to find and reallocate a larger space first, and then copy all the data over; time complexity $O(n)$.