---
title: Sets
description: 
published: true
date: 2020-08-09T02:29:42.355Z
tags: mathematics, set-theory
editor: markdown
---

# Set
A set is a well-defined collection of distinct objects in no particular order. 


A powerset of a set *S* is the set of all subsets of S. It can be calculated with the following algorithm: 

*Tail down a list recursively, mapping over the rest of
the list and appending the result of adding the head of the current list to each item in the rest of the list..* 


`// in pseudocode`
`function powerset(S) {`
`	if (is_null(S)) {`
`  	return null;`
`  }`
`  const rest = powerset(tail(S));`
`  return append(rest, map((item)=>{`
`  	return pair(head(S), item);`
`  }, rest));`
`}`