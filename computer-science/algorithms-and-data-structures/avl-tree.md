---
title: AVL Tree
description: 
published: true
date: 2022-05-01T23:18:56.665Z
tags: data-structures, trees
editor: markdown
---

# AVL Tree
This is a self-balancing Binary Search Tree, where the difference between the heights of left and right subtrees cannot be more than one for all nodes. 

Most of the BST operations (e.g., search, max, min, insert, delete.. etc) take O(h) time where h is the height of the BST. 

If we make sure that height of the tree remains O(Logn) after every insertion and deletion, then we can guarantee an upper bound of O(Logn) for all these operations. The height of an AVL tree is always O(Logn) where n is the number of nodes in the tree.
## Node Structure
```
typedef struct AVLNode {
    void *data;
    struct AVLNode *left;
    struct AVLNode *right;
    int height;
} AVLNode;
```

## Insertion (Recursive)
1. Start with standard BST insertion. (recursively traverse the tree until the proper location of insertion is found, using the (keys(left) < key(root) < keys(right) property of the BST) 

2. While we are traversing down the tree to find and insert our new node, when we finally insert our node, due to the recursive nature of the function, the ancestor node's heights will be updated starting from the parent of the new node all the way up to the root. At each level, after the height is updated, we check to see if the balance of the tree violates the constraints of the AVL tree. 


3. During this traverse up from the newly inserted node back to root, we also are checking if we need and then performing rebalancing of the tree. 

	Let z be the first unbalanced node, y be the child of z that comes on the path from w to z and x be the grandchild of z that comes on the path from w to z. 
  
    Re-balance the tree by performing appropriate rotations on the subtree rooted with z. There can be 4 possible cases that needs to be handled as x, y and z can be arranged in 4 ways. Following are the possible 4 arrangements: 
	a) y is left child of z and x is left child of y 
  
  ```
  (Left Left Case)
  T1, T2, T3 and T4 are subtrees.
         z                                      y 
        / \                                   /   \
       y   T4      Right Rotate (z)          x      z
      / \          - - - - - - - - ->      /  \    /  \ 
     x   T3                               T1  T2  T3  T4
    / \
  T1   T2
  ```
  
  
	b) y is left child of z and x is right child of y
  ```
  (Left Right)
    z                               z                           x
    / \                            /   \                        /  \ 
   y   T4  Left Rotate (y)        x    T4  Right Rotate(z)    y      z
  / \      - - - - - - - - ->    /  \      - - - - - - - ->  / \    / \
T1   x                          y    T3                    T1  T2 T3  T4
    / \                        / \
  T2   T3                    T1   T2
```
	c) y is right child of z and x is right child of y 
  ```
  (Right Right Case) 
    z                                y
 /  \                            /   \ 
T1   y     Left Rotate(z)       z      x
    /  \   - - - - - - - ->    / \    / \
   T2   x                     T1  T2 T3  T4
       / \
     T3  T4
  
  ```
	d) y is right child of z and x is left child of y
  ```
  (Right Left Case)
     z                            z                            x
  / \                          / \                          /  \ 
T1   y   Right Rotate (y)    T1   x      Left Rotate(z)   z      y
    / \  - - - - - - - - ->     /  \   - - - - - - - ->  / \    / \
   x   T4                      T2   y                  T1  T2  T3  T4
  / \                              /  \
T2   T3                           T3   T4
  ```
  
## Insertion ( C Implementation )
```
struct Node* insert(struct Node* node, int key)
{
    /* 1.  Perform the normal BST insertion */
    if (node == NULL)
        return(newNode(key));
 
    if (key < node->key)
        node->left  = insert(node->left, key);
    else if (key > node->key)
        node->right = insert(node->right, key);
    else // Equal keys are not allowed in BST
        return node;
 
    /* 2. Update height of this ancestor node */
    node->height = 1 + max(height(node->left),
                           height(node->right));
 
    /* 3. Get the balance factor of this ancestor
          node to check whether this node became
          unbalanced */
    int balance = getBalance(node);
 
    // If this node becomes unbalanced, then
    // there are 4 cases
 
    // Left Left Case
    if (balance > 1 && key < node->left->key)
        return rightRotate(node);
 
    // Right Right Case
    if (balance < -1 && key > node->right->key)
        return leftRotate(node);
 
    // Left Right Case
    if (balance > 1 && key > node->left->key)
    {
        node->left =  leftRotate(node->left);
        return rightRotate(node);
    }
 
    // Right Left Case
    if (balance < -1 && key < node->right->key)
    {
        node->right = rightRotate(node->right);
        return leftRotate(node);
    }
 
    /* return the (unchanged) node pointer */
    return node;
}
```

## Program Flow of above recursive implementation
Inserting 30 into a tree containing [10, 20] for example would have the following execution order:

1) From the root of 10, traverse to the right child, which is 20. 
2) From 20, traverse to the right child, which is NULL
3) We insert 30
4) We are back in in the recursive call from step 2, so we adjust the height of 30's parent node 20. We check if the tree is unbalanced at this point, and its not. 
5) We are back in the recursive call from step 1, so we adjust the height of 20's parent node 10 (which is 30's GRANDparent node). We see that the tree is now unbalanced, we are in the right right case, so we perform the necessary rotations.


So in general, when we are recursing, we
recurse->recurse->recurse (until the innermost function returns, and we exit back out the way we came, adjusting heights and setting 
  
    