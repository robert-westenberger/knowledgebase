---
title: Storing Hierarchical Structures In A Relational Database
description: 
published: true
date: 2021-11-30T17:52:27.202Z
tags: computer-science
editor: markdown
---

# Ajacency List
* Storing the parent ID
* This is an **anti pattern.** 
* Expensive to retreieve ancestors of a given node in the tree (such as the root node)
# Closure Table
A closure table stores all paths through the tree, not just those with a direct parent-child relationship.

In addition to whichever table contains a hierarchical self reference(for example, `Node`), we need to add a table that will store the hierarchical information.

The table storing the hierarchical information (for example, `NodePaths`) will need to have two columns, each of which is a foreign key to rows in the `Node` table.

So for every descendant of a particular node, including the node itself, it will need an entry in the `nodePaths` table.

The below two tables show what a directory structure would look like in SQL utilizing a closure table. 

**Directory**
| id | parent_dir | name |
| :--- | :--- | :--- |
| 1 | 0 | A |
| 2 | 1 | B |
| 3 | 2 | C |

**Directory Closures**
| parent | child | depth |
| :---: | :---: | :---: |
| 1 | 1 | 0 |
| 2 | 2 | 0 |
| 3 | 3 | 0 |
| 1 | 2 | 1 |
| 2 | 3 | 1 |
| 1 | 3 | 2 |


Note that the total number of records in the closure table is equal to the number of records in the base table, times the average depth of the tree(s) in the base table. (That is, each base table row has a row in the closure table, plus one row for each of its parents.)

## Inserting a child
```
insert into closure(parent, child, depth)
select p.parent, c.child, p.depth+c.depth+1
  from closure p, closure c
 where p.child=PARENT_ITEM and c.parent=CHILD_ITEM
 ```
 
