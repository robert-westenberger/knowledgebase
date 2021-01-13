---
title: 2.3.3 Example: Representing Sets
description: 
published: true
date: 2021-01-13T02:36:11.742Z
tags: book-notes
editor: markdown
---

# 2.3.3 Example: Representing Sets
A set is a collection of distinct objects. Operations involving sets include 
* is_element_of_set - determines whether a given element is a member of a set.
* adjoin_set - takes an object and a set as args and returns a set that contains elements of the original set and also the adjoined element.
* union_set - computes the set containing each element that appears in either argument.
* intersection_set - computes the set containing each element that appear in both arguments.

If a set is represented as an **ordered list**, we no longer have to scan the entire list.. if we reach an element that is larger than the element we are searching for then we know it's not in the list.