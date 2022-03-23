---
title: Databases QA
description: 
published: true
date: 2022-03-23T16:30:38.063Z
tags: backend, interviewing, databases
editor: markdown
---

# What is normalisation?
Normalization is basically to design a database schema such that duplicate and redundant data is avoided. If the same information is repeated in multiple places in the database, there is the risk that it is updated in one place but not the other, leading to data corruption.

There is a number of normalization levels from 1. normal form through 5. normal form. Each normal form describes how to get rid of some specific problem.

By having a database with normalization errors, you open the risk of getting invalid or corrupt data into the database. Since data "lives forever" it is very hard to get rid of corrupt data when first it has entered the database.