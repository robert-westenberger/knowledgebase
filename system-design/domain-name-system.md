---
title: Domain Name System
description: 
published: true
date: 2022-04-02T21:33:09.175Z
tags: system-design
editor: markdown
---

# How does DNS Work?
A Domain Name System translates a domain name such as `www.example.com` to an IP address. 

DNS is hierarchical, with a few authoritative servers at the top level. Your router or ISP provides information about which DNS server(s) to contact when doing a lookup. Lower level DNS servers cache mappings, which could become stale due to DNS propagation delays. DNS results can also be cached by your browser or OS for a certain period of time, determined by time to live (TTL).

## Time to live / hop limit
Time to live / hop limit is a mechanism which limits the lifespan or lifetime of data in a computer network. It may be implemented as a counter or timestamp attached to or embedded in the data. Once the event count or timespan has elapsed, data is discarded or revalidated.

