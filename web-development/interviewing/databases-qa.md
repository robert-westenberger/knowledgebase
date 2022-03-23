---
title: Databases QA
description: 
published: true
date: 2022-03-23T16:37:07.005Z
tags: backend, interviewing, databases
editor: markdown
---

# What is normalisation?
Normalization is basically to design a database schema such that duplicate and redundant data is avoided. If the same information is repeated in multiple places in the database, there is the risk that it is updated in one place but not the other, leading to data corruption.

There is a number of normalization levels from 1. normal form through 5. normal form. Each normal form describes how to get rid of some specific problem.

By having a database with normalization errors, you open the risk of getting invalid or corrupt data into the database. Since data "lives forever" it is very hard to get rid of corrupt data when first it has entered the database.

# What are the advantages of NoSQL over traditional RDBMS?

NoSQL is better than RDBMS because
- It supports semi-structred data and volatile data
- It does not have schema
- Read/Write throughput is very high
- High horizontal scalability
- Will support Bigdata in volumes of Terra Bytes & Peta Bytes
- Provides good support for Analytic tools on top of Bigdata
- Can be hosted in cheaper hardware machines
- In-memory caching option is available to increase the performance of queries
- Faster development life cycles for developers

RDBMS is better 
- Transactions with atomicity, consistency, isolation, and durability
- Adherence to a strong schema of data being written, read.
- Real time query management
- Execution of complex queries involving join and group by clauses.

# Define ACID properties
# How can a database index help performance?
# What's the cost of having a database index?
# What are some types of indexes?
# What is denormalization?
# What's the difference between a primary key and a unique key?
# What is sharding?
# How do you offload work from the database?
