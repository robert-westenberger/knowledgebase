---
title: NodeJS QA
description: 
published: true
date: 2022-03-24T16:45:18.526Z
tags: backend, interviewing, node
editor: markdown
---

# What is nodejs?
It's an asynchronous, single threaded event-driven javascript runtime. It's designed to build scalable network applications. 

# What is an error-first callback?
A callback whose first argument is an error object the user has to check if something went wrong. Additional arguments are used to pass data.

# What is callback hell?
Deeply nested callbacks. In order to get out of callback hell, some good solutions are to

1. Use Promises (can chain together .then() ) statements
2. Use Async/await

# What are the key features of NodeJS?
- **Asynchronous event driven IO helps concurrent request handling**
- **Single threaded but highly scalable**: A single request doesn't block the processing of other requests. 
- It uses javascript
- No buffering of data (what does this actually mean?)


