---
title: Caching QA
description: 
published: true
date: 2022-03-23T16:16:48.455Z
tags: backend, interviewing, caching
editor: markdown
---

# What is caching?
A high-speed data storage layer which stores a subset of data, typically transient in nature, so that future reqeusts for that data are served up faster than is possible by accessing the data's primary storage location. 

Allows you to efficiently reuse previously retrieved or computed data.

# Is Redis just a cache?
Like a cache Redis offers:
- in memory key-value storage
But unlike a cash Redis:
- Supports multiple datatypes (strings, hashes, lists, sets, sorted sets, bitmaps, and hyperloglogs)
- It provides an ability to store cache data into physical storage (if needed).
- Supports pub-sub model
- Redis cache provides replication for high availability (master/slave)
- Supports ultra-fast lua-scripts. Its execution time equals to C commands execution.
- Can be shared across multiple instances of the application (instead of in-memory cache for each app instance)

# What is Resultset Caching?
Storing the results of a database query along with the query in the application. Every time a web page generates a query, the applications checks whether the results are already cached, and if they are, pulls them from an in-memory data set instead. The application still has to render the page.