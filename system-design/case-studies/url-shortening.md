---
title: URL Shortening Service
description: 
published: true
date: 2022-03-29T01:23:05.539Z
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