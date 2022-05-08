---
title: Tree Traversals
description: 
published: true
date: 2022-05-08T21:16:10.243Z
tags: algorithms, trees
editor: markdown
---

# Depth First
## Inorder (Left, Root, Right)
### Algorithm
   1. Traverse the left subtree, i.e., call Inorder(left-subtree)
   2. Visit the root.
   3. Traverse the right subtree, i.e., call Inorder(right-subtree)
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
### Implementation
#### Javascript
```

function treeByLevels (rootNode) {
  const returnArray = [];
  const queue = [];
  if (rootNode !== null) {
    queue.push(rootNode);
  }
  
  while (queue.length !== 0) {
    const node = queue.shift();
    returnArray.push(node.value);
    if (node.left !== null) {
      queue.push(node.left);
    }
    if (node.right !== null) {
      queue.push(node.right);
    }
  }

	return returnArray;
}
```


