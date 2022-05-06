---
title: Construct  Binary Search Tree From Given Preorder Traversal
description: 
published: true
date: 2022-05-06T22:43:12.250Z
tags: algorithms, binary-trees, binary-search-trees
editor: markdown
---

# Problem
Given an array of integers preorder, which represents the preorder traversal of a BST (i.e., binary search tree), construct the tree and return its root.

It is guaranteed that there is always possible to find a binary search tree with the given requirements for the given test cases.

A binary search tree is a binary tree where for every node, any descendant of Node.left has a value strictly less than Node.val, and any descendant of Node.right has a value strictly greater than Node.val.

A preorder traversal of a binary tree displays the value of the node first, then traverses Node.left, then traverses Node.right.

# Approach
## Implementation (Javascript)
```
const constructBST = (preorder, size, position, current, left, right, level) => {

    if (position === size || preorder[position] < left || preorder[position] > right) {
        return position;
    }
    
    if (preorder[position] < current.val) {
        current.left = new TreeNode(preorder[position]);
        position += 1;
        position = constructBST(preorder, size, position, current.left, left, current.val - 1);
    }
    
    if (position === size || preorder[position] < left || preorder[position]>right){
        return position;
    }
    
    current.right = new TreeNode(preorder[position]);
    position+= 1;
    position = constructBST(preorder, size, position, current.right, current.val + 1, right);
    return position;
}
const bstFromPreorder = function(preorder) {
    const size = preorder.length;
    if (size === 0) {
        return null;
    }
    const root = new TreeNode(preorder[0]);
    if (size === 1) {
        return root;
    }
    constructBST(preorder, size, 1, root, Number.MIN_SAFE_INTEGER, Number.MAX_SAFE_INTEGER);
    return root;
};
```
### Example 
With a preorder of [8, 5, 1, 7, 10, 12]

We make 8 the root of the BST, and call `constructBST` function for the first time.

`CALL 1: constructBST(preorder, size, 1, root, Number.MIN_SAFE_INTEGER, Number.MAX_SAFE_INTEGER, 0);`
**START CALL 1 EXECUTION**
Size is 6.
preorder[position] is 5
current.val is 8

preorder[position] < current.val evaluates to true, so we insert 5 to the left of the root 8. 

position is incremented to 2. 

We make another call to get the value of positon.

`position = CALL 2: constructBST(preorder, size, 2, current.left, left, current.val - 1 = 7);`
**START CALL 2 EXECUTION**
preorder[position] is 1
current.val is 5

preorder[position] < current.val evaluates to true, so we insert 1 to the left of the 5 node.

position is incremented to 3.

We make another call to get the value of position.

`position = CALL 3: constructBST(preorder, size, 3, current.left, left, current.val - 1 = 4);`
**START CALL 3 EXECUTION**
preorder[position] is 7
current.val is 1

preorder[position] > right evaluates to true, so we return position, which is 3.
**END CALL 3 EXECUTION**
preorder[position] = 7
current.val is still 5

We place 1 as 5's right node. 

Position is incremeted to 4.

We make another call to get the value of position.

`position= CALL 4: constructBST(preorder, size, 4, current.right, current.val + 1 = 6, right = 7)`

**START CALL 4 EXECUTION**
preorder[position] = 10
current.val = 7 

preorder[position] > right = true, so we return position (4)

**END CALL 4 EXECUTION**
return 4 position
**END CALL 2 EXECUTION**
preorder[position] = 10
current.val = 8 (we are back at root)

We push 10 to be the right child of root.

increment position to 5

We make another call to get the value of position
`position=CALL 5: constructBST(preorder, size, 5, current.right, current.val + 1 (9), right (max int))`
**START CALL 5 EXECUTION**
current.val = 10
preorder[position] = 12

we make 12 the right child of 10
we increment position
we make another call to get the value of position
`position=CALL 6: constructBST(preorder, size, 6, current.right, current.val + 1 (12), right (max int))`
**START CALL 6 EXECUTION**
position === size, so we return 6
**END CALL 6 EXECUTION**
We return 6
**END CALL 5 EXECUTION**
We return 6. The tree is now fully constructed.
**END CALL 1 EXECUTION**


