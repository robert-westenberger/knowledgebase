---
title: Availability & Reliability QA
description: 
published: true
date: 2022-03-23T16:11:21.294Z
tags: backend, interviewing
editor: markdown
---

# What is Availability?
Refers to the probability that a system performs correctly at a specific time instance (not duration). Interruptions may occur before or after the time instance for which the system's availability is calculated. The service must be operational and adequately satisfy the defined specifications at the time of its usage.

It's often quantified by uptime (or downtime) as a % of time the service is available (99.99% uptime)

# What is Reliability?
Probability that a system performs correctly during a specific time duration.

During this correct operation, no repair is required or performed, and the system adequately follows the defined performance specifications.

Reliability follows an exponential failure law, which means that it reduces as the time duration considered for reliability calculations elapses. In other words, reliability of a system will be high at its initial state of operation and gradually reduce to its lowest magnitude over time.

# What is Failover?
The ability to seamlessly and automatically switch to a reliable backup system. 

A redundant or standby database server, system, or other hardware component, server, or network should be ready to replace any previously active version upon its abnormal termination or failure. 