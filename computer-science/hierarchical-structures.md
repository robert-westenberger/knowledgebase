---
title: Storing Hierarchical Structures In A Relational Database
description: 
published: true
date: 2021-11-30T01:13:08.125Z
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