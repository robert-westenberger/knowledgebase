---
title: System Design Interviews
description: 
published: true
date: 2022-03-28T23:41:11.670Z
tags: interviewing, system-design
editor: markdown
---

# Overview 
## Step 1: Requirements clarifications and alignment

## Step 2: Back-of-the-envelope-estimation
Always a good idea to estimate the scale of the system we're going to esign. This will help later when we focus on scaling, partitioning, load balancing, and caching. 

## Step 3: System Interface Design
Define what APIs are expected from the system. 

## Defining data model
Defining the data model in the early part of the interview will clarify how data will flow between different system components. 

Later, it will guide for data partitioning and management. The candidate should identify various system entities, how they will interact with eachother, and different aspects of data management like storage, transporation, encryption, etc.

Which database system should we use? Will NoSQL, or a relational database better fit our needs? What kind of block storage should we use to store photos and videos?
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

## Defining data model
**User:** UserID, Name, Email, DoB, CreationDate, LastLogin, etc.
**Tweet:** TweetID, Content, TweetLocation, NumberOfLikes, TimeStamp, etc.
**UserFollow:** UserID1, UserID2
**FavoriteTweets:** UserID, TweetID, TimeStamp
