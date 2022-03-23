---
title: Concurrency QA
description: 
published: true
date: 2022-03-23T16:26:56.323Z
tags: backend, interviewing, concurrency
editor: markdown
---

# What is a mutex?
Mutually exclusive flag. Acts as a gatekeeper to synchronize two threads. 

When you have two threads attempting to access a single resource, the general pattern is to have the first block of code attempting access, to set the mutex before entering the code. When the second code block attempts access, it sees that the mutex is set and waits until the first block of code is complete (and un-sets the mutex), then continues.

# What is Deadlock?
- A **lock** occurs when multiple processes try to access the same resource at the same time. One process loses out and must wait for the other to finish. 
- A **deadlock** occurs when the waiting process is still holding on to another resource that the first needs before it can finish.

# What is the meaning of the term "Thread-Safe"?

