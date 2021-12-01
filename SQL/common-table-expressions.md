---
title: Common Table Expressions (in SQLITE)
description: 
published: true
date: 2021-12-01T18:11:33.486Z
tags: 
editor: markdown
---

# Subqueries
Starting with a simple query

```
SELECT 1
```

This will return `1`. 

The following is a very simple subquery.

```
SELECT * FROM (SELECT 1);
```

The above will select all of the results from our subquery, which in this case, is a single row. 
# Common Table Expressions
A **common table expression** is basically the same as a subquery, except assigned a name and defined prior to the query in which it's referenced. 

The simplest CTE version of the above query would be 

```
WITH one AS (SELECT 1)
SELECT * FROM one;
```

In the above, the common table expression is named "one". It is filled with the output of `SELECT 1`, which is one row.  Then, we select everything from "one", which again is just that one row. 

## CTE's can have multiple columns
```
WITH twoCol( a, b ) AS ( SELECT 1, 2 )
SELECT a, b FROM twoCol;
```
The above will return 1 row with an `a` column and a `b` column.