---
title: Domain Name System
description: 
published: true
date: 2022-04-02T21:30:50.230Z
tags: system-design
editor: markdown
---

# How does DNS Work?
A Domain Name System translates a domain name such as `www.example.com` to an IP address. 

DNS is hierarchical, with a few authoritative servers at the top level. Your router or ISP provides information about which DNS server(s) to contact when doing a lookup. Lower level DNS servers cache mappings, which could become stale due to DNS propagation delays. DNS results can also be cached by your browser or OS for a certain period of time, determined by time to live (TTL).

