---
title: Section 3.3 Modeling with Mutable Data
description: 
published: true
date: 2020-12-24T07:33:59.707Z
tags: book-notes
editor: markdown
---

# Modeling with Mutable Data

In order to model compound objects with changing state, we will design data abstractions to include, in addition to selectors and constructors, operations called *mutators*, which modify data objects. Data objects that have mutators are *mutable data objects*. 

### Sharing and identity
Sharing is undetectable if data objects are not mutated. However if two different data objects contain members that point to the same piece of data in memory; mutating data for one object that points 

