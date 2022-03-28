---
title: System Design Interviews
description: 
published: true
date: 2022-03-28T23:36:49.294Z
tags: interviewing, system-design
editor: markdown
---

# Overview 
## Step 1: Requirements clarifications and alignment

## Step 2: Back-of-the-envelope-estimation
Always a good idea to estimate the scale of the system we're going to esign. This will help later when we focus on scaling, partitioning, load balancing, and caching. 
### Example: Designing Twitter
- What scale is expected from the system? (number of new tweets, number of tweet views, number of timeline generations per second)
- How much storage will we need? We will have different requirements if users can have photos and videos in their tweets.
- What network bandwidth usage are we expecting? This will be crucial in deciding how we will manage traffic and balance load between servers.

## Step 3: System Interface Design
Define what APIs are expected from the system. 

# Example Designing Twitter
## Requirements Clarifications
- Will users of our service be able to post tweets and follow other people?
- Should we also design to create and display the user’s timeline?
- Will tweets contain photos and videos?
- Are we focusing on the backend only, or are we developing the front-end too?
- Will users be able to search tweets?
- Do we need to display hot trending topics?
- Will there be any push notification for new (or important) tweets?

## Back-of-the-envelope-estimation
- What scale is expected from the system? (number of new tweets, number of tweet views, number of timeline generations per second)
- How much storage will we need? We will have different requirements if users can have photos and videos in their tweets.
- What network bandwidth usage are we expecting? This will be crucial in deciding how we will manage traffic and balance load between servers.
