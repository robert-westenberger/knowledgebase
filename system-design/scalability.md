---
title: Scalability
description: 
published: true
date: 2022-04-02T20:53:47.977Z
tags: system-design
editor: markdown
---

# Vertical Scaling
Vertical scaling means increasing the amount of power on a single machine. It would be like building a tower taller and taller, where the height of the tower represents power of server resources.

## Pros of vertical scaling
* It's easier to implement. You don't need to modify any of your code, it's just a matter of paying more money for better hardware.
## Drawbacks to vertical scaling
* It poses a higher risk for downtime, since there is a single point of failure. 

# Horizontal Scaling
Horizontal scaling adds more instances of machines of weaker power. 

Horizontal scaling is more challenging, because it requires breaking a sequential piece of logic into smaller pieces so that they can be executed in parallel across multiple machines. 