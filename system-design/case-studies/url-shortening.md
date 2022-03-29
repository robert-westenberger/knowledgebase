---
title: URL Shortening Service
description: 
published: true
date: 2022-03-29T01:34:22.882Z
tags: interviewing, system-design
editor: markdown
---

# Why do we need URL shortening?
Short links that redirect to longer URLs are useful because they 
- Save a lot of space when displayed, printed, messaged, or tweeted. 
- Optimize links across devices
- Track individual links to analyze audience, measure ad campaign's performance
- Hide affiliated URLs

# Requirements
## Functional Requirements
1. Given a URL, our service should generate a shorter and unique alias of it. It sohuld be short enough to be easily copied and pasted into applications.
2. When users access a short link, our service should redirect them to the original link.
3. Users should optionally be able to pick a custom short link for their URL.
4. Links will expire after a standard default timespan. Users should be able to specify the expiration time.

## Nonfunctional requirements
1. It should be highly available. If our service is down, all the URL redirections will start failing.
2. Redirection should happen in real time with minimal latency.
3. Shortened links should not be guessable/predictable.

## Extended requirements
1. Analytics (how many times a redirection happened?)
2. Should be accessible through REST APIs by other services.

# Capacity Estimation and Constraints
The system will be read-heavy. There will be lots of redirection requests compared to new URL shortenings. 

We can assume a 100:1 ratio between read and write.

## Traffic Estimates
Assuming we have 500m new URL shortenings per month, we can expect 50b redirections in the same period. 

### Queries Per Second
500m / (30 days * 24 hours * 3600 seconds) = ~200 new URLs / second

Considering a 100:1 read/write ratio, redirections would be 20,000 per second.