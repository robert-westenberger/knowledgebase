---
title: System Design Interviews
description: 
published: true
date: 2022-03-29T00:59:59.086Z
tags: interviewing, system-design
editor: markdown
---

# Overview 
## Step 1: Requirements clarifications and alignment

## Step 2: Back-of-the-envelope-estimation
Always a good idea to estimate the scale of the system we're going to esign. This will help later when we focus on scaling, partitioning, load balancing, and caching. 

## Step 3: System Interface Design
Define what APIs are expected from the system. 

## Step 4: Defining data model
Defining the data model in the early part of the interview will clarify how data will flow between different system components. 

Later, it will guide for data partitioning and management. The candidate should identify various system entities, how they will interact with eachother, and different aspects of data management like storage, transporation, encryption, etc.

Which database system should we use? Will NoSQL, or a relational database better fit our needs? What kind of block storage should we use to store photos and videos?

## Step 5: High-level design
Draw a block diagram with 5-6 boxes representing the core components of our system. We should identify enough components that are needed to to solve the actual problem from end to end.

## Step 6: Detailed Design
Interviewer's feedback should guide us to what parts of the system need further discussion. 

Different approaches should be presented, and their pros and cons, and explain why we prefer one approach over the other. 

## Step 7: Identifying and Resolving Bottlenecks
Try and discuss as many bottlenecks as possible and different approaches to mitigate them. 


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

## High-level design
For Twitter, we need multiple application servers to serve all the read/write requests with load balancers in front of them for traffic distributions. If we're assuming that we will have a lot more read traffic (compare to write), we can decide to have separate servers to handle this. 

On the backend, we need an efficient database that can store all the tweets and support a large number of reads. We'll also need a distributed file storage system for storing photos and videos.
![twitter_structure.png](/twitter_structure.png)

## Detailed design
- Since we will be storing a massive amount of data, how sohuld it be partitioned to distribute it to multiple databases? Should we try to store all the data of a user on the same database? What issue could it cause?
- How will we handle hot users who tweet a lot or follow lots of people?
- Since user's timeline will contain the most recent / relevant tweets, should we try to store our data so that it is optimized for scanning the latest tweets?
- How much and at which layer should we introduce cache to speed things up?
- What components need better load balancing?