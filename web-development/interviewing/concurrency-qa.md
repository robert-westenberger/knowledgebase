---
title: Concurrency QA
description: 
published: true
date: 2022-03-23T16:24:03.463Z
tags: backend, interviewing, concurrency
editor: markdown
---

# What is a mutex?
Mutually exclusive flag. Acts as a gatekeeper to synchronize two threads. 

When you have two threads attempting to access a single resource, the general pattern is to have the first block of code attempting access, to set the mutex before entering the code. When the second code block attempts access, it sees that the mutex is set and waits until the first block of code is complete (and un-sets the mutex), then continues.