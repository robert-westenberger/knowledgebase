---
title: Data Intensive Applications
description: 
published: true
date: 2022-06-10T17:04:57.369Z
tags: system-design
editor: markdown
---

# Reliability
Reliability means making systems work correctly, even when faults occur. 

Faults can be in hardware (typically random and uncorrelated), software (bugs are typically systematic and hard to deal with), and humans (who inevitably make mistakes from time to time). 

Fault-tolerance techniques can hide certain types of faults from the end user.


# Scalability
Scalability means having strategies for keeping performance good, even when load increases. 

In order to discuss scalability, we first need ways of describing load and performance quantitatively.

## Describing Load
# Maintainability
Maintainability has many facets, but in essence it’s about making life better for the engineering and operations teams who need to work with the system.

Good abstractions can help reduce complexity and make the system easier to modify and adapt for new use cases. 

Good operability means having good visibility into the system’s health, and having effective ways of managing it.