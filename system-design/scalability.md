---
title: Scalability
description: 
published: true
date: 2022-04-02T21:02:03.085Z
tags: system-design
editor: markdown
---

# Vertical Scaling
Vertical scaling means increasing the amount of power on a single machine. It would be like building a tower taller and taller, where the height of the tower represents power of server resources.

## Databases
The data lives on a single node, and scaling is done thorugh multi-core, e.g. spreading the load between the CPU and the RAM resources of the machine.

## Downtime 
Vertical scaling is limited to one machine. Scaling beyond that capacity can involve downtime and has a hard upper limit, which is the scale of the hardware on which you are currently running.

## Concurrency
Concurrent programming on multi-core machines are often performed via multi-threading and inprocess message passing.
## Pros of vertical scaling
* It's easier to implement. You don't need to modify any of your code, it's just a matter of paying more money for better hardware.
## Drawbacks to vertical scaling
* It poses a higher risk for downtime, since there is a single point of failure. 

# Horizontal Scaling
Horizontal scaling adds more instances of machines of weaker power. 

Horizontal scaling is more challenging, because it requires breaking a sequential piece of logic into smaller pieces so that they can be executed in parallel across multiple machines. 


## Databases
In a database world, horizontal scaling is usually based on the partitioning of data ( each node only contains part of the data ).
## Downtime
In theory, adding more machines to the existing pool means you are not limited to the capacity of a single unit. There isn't a single point of failure, so there is less downtime compared to a purely vertical scaling approach. Also, you don't need to power off one machine to upgrade it. 

