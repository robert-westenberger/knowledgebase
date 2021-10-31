---
title: Detect Loop In Linked List
description: 
published: true
date: 2021-10-31T03:10:55.124Z
tags: algorithms
editor: markdown
---

# Hashing Approach

Traverse the list one by one and keep putting the node addresses in a Hash Table. At any point, if NULL is reached then return false, and if the next of the current nodes points to any of the previously stored nodes in  Hash then return true.

# Floyd's Cycle-Finding Algorithm