---
title: Data Intensive Applications
description: 
published: true
date: 2022-06-10T17:33:28.027Z
tags: system-design
editor: markdown
---

# Reliability, Scalability, and Maintainability
## Reliability
Reliability means making systems work correctly, even when faults occur. 

Faults can be in hardware (typically random and uncorrelated), software (bugs are typically systematic and hard to deal with), and humans (who inevitably make mistakes from time to time). 

Fault-tolerance techniques can hide certain types of faults from the end user.


## Scalability
Scalability means having strategies for keeping performance good, even when load increases. 

In order to discuss scalability, we first need ways of describing load and performance quantitatively.

### Describing Load
Load can be described with **load parameters**. The best choice of parameters depends on the architecture of your system. It may be requests per second to a web server, the ratio of reads to writes in a database, the number of simultaneously active users in a chat room, the hit rate on a a cache, or something else. 

### Describing Performance
Once you have described the load on your system, you can investigate what happens when the load increases. Yo ucan look at it in two ways: 
- When you increase a load parameter and keep the system resources (CPU, memory, network bandwidth, etc.) unchanged, how is the performance of your system affected?

- When you increase a load parameter, how much do you need to increase the resources if you want to keep performance unchanged?
## Maintainability
Maintainability has many facets, but in essence it’s about making life better for the engineering and operations teams who need to work with the system.

Good abstractions can help reduce complexity and make the system easier to modify and adapt for new use cases. 

Good operability means having good visibility into the system’s health, and having effective ways of managing it.

# Data Models and Query Languages