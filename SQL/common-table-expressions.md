---
title: Common Table Expressions
description: 
published: true
date: 2021-12-01T17:54:01.394Z
tags: 
editor: markdown
---

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