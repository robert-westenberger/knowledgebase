---
title: Tree Traversals
description: 
published: true
date: 2022-04-26T17:39:54.131Z
tags: algorithms, trees
editor: markdown
---

# Breadth-First or Level Order Traversal
For a tree of 
<pre>
     1
    / \  
   2   3
  / \
 4   5
</pre>
A breadth-first traversal would be 1 2 3 4 5
## Algorithm
```
printLevelorder(tree)
1) Create an empty queue q
2) temp_node = root /*start from root*/
3) Loop while temp_node is not NULL
    a) print temp_node->data.
    b) Enqueue temp_node’s children 
      (first left then right children) to q
    c) Dequeue a node from q.
```
