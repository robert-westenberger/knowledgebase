---
title: Common Table Expressions (in SQLITE)
description: 
published: true
date: 2021-12-01T18:48:52.186Z
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

## CTE's can query other tables
```
CREATE TABLE foo ( bar INTEGER);
INSERT INTO foo VALUES(1);
INSERT INTO foo VALUES(2);

WITH fooCTE AS (SELECT * FROM foo)
  SELECT * FROM fooCTE;
```
## Multiple CTE's can be defined for a single query:
```
WITH aCTE AS (SELECT 'a'), 
bCTE AS (SELECT 'b')
SELECT * FROM aCTE, bCTE;
```

## Compound Select Statements
```
WITH RECURSIVE ten(x) AS ( 
	SELECT 1 
  	UNION ALL 
  SELECT x+1 FROM ten WHERE x<10 
)
SELECT * FROM ten;
```
The above will generate a table containing the numbers 1 through 10. The CTE named 10, with a column name of `x` (the column name is optional, but in this case we need to refer to it later). Then in the recursive UNION ALL, we keep adding one more row to the result set, each one larger than the row before, until we reach a limit of 10. 

## Transformations on Data
CTE's are essentially a programming language that can be used to perform complex transformations on data, such as converting a comma-separated list into a table that can be joined against. 
```
WITH RECURSIVE list( element, remainder ) AS (
	SELECT NULL AS element, '1,2,3,4,5' AS remainder
		UNION ALL
	SELECT
  	CASE
    	WHEN INSTR( remainder, ',' )>0 THEN 
      	SUBSTR( remainder, 0, INSTR( remainder, ',' ) )
      ELSE
        remainder
     END AS element,
     CASE
     		WHEN INSTR( remainder, ',' )>0 THEN 
      		SUBSTR( remainder, INSTR( remainder, ',' )+1 )
      	ELSE
      		NULL
     END AS remainder
   FROM list
   WHERE remainder IS NOT NULL
)
SELECT element FROM list WHERE element IS NOT NULL;
```
* In the above, imagine a table with two columns: element, and remainder. The “element” of each row contains a single element of the list, whereas “remainder” contains everything that comes after it.

* We start off by seeding the table with a single row containing a NULL element, and a “remainder” containing the list we want to transform: “1,2,3,4,5”

* Then we define the recursive CTE to generate a new row containing the first element of the list (everything before the first comma), and the remainder (everything after the first comma)

* Unfortunately sqlite doesn’t support the IF syntax, so I’m using the slightly more confusing (but way more powerful) CASE syntax, but basically it’s saying “if there is a comma, then everything before is an element, and everything after is the remainder. If there is no comma, then the whole thing is the element, and there is no remainder.”

* Finally, it says “keep recursing until there is no more remainder”

* The result is a table containing one row per element, plus one NULL element (which is what we seeded the CTE’s result table with)

* So we select everything except for that NULL element, and voila, we’ve converted a comma-separated list into a table, purely in SQL.

## Hierarchical Queries
Consider for example a company's expense report approval hierarchy. The approval structure for any specific employee is b oth their approver, their approver's approver, etc, until you reach someone that has no approver.

```
CREATE TABLE company ( name, approver );

INSERT INTO company VALUES ( 'David', NULL ), ( 'Matt', 'David' ), ( 'Jason', 'David' ), ( 'Ryan', 'David' ), ( 'Mike', 'Matt' ), ( 'Carlos', 'Matt' ), ( 'Garrett', 'Jason' ), ( 'Puneet', 'Jason' ), ( 'Joanie', 'Ryan' );
```

```
WITH RECURSIVE approvers(x) AS (
	SELECT 'Joanie' 
		UNION ALL
  SELECT company.approver 
  FROM company, approvers 
  WHERE company.name=approvers.x AND company.approver IS NOT NULL
)
SELECT * FROM approvers;
```