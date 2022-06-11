---
title: Data Intensive Applications
description: 
published: true
date: 2022-06-11T22:57:59.331Z
tags: system-design
editor: markdown
---

# Reliability, Scalability, and Maintainability
## Reliability
Reliability means making systems work correctly, even when faults occur. 

Faults can be in hardware (typically random and uncorrelated), software (bugs are typically systematic and hard to deal with), and humans (who inevitably make mistakes from time to time). 

Fault-tolerance techniques can hide certain types of faults from the end user.


## Scalability
Scalability means having strategies for keeping performance good, even when load increases. 

In order to discuss scalability, we first need ways of describing load and performance quantitatively.

### Describing Load
Load can be described with **load parameters**. The best choice of parameters depends on the architecture of your system. It may be requests per second to a web server, the ratio of reads to writes in a database, the number of simultaneously active users in a chat room, the hit rate on a a cache, or something else. 

### Describing Performance
Once you have described the load on your system, you can investigate what happens when the load increases. Yo ucan look at it in two ways: 
- When you increase a load parameter and keep the system resources (CPU, memory, network bandwidth, etc.) unchanged, how is the performance of your system affected?

- When you increase a load parameter, how much do you need to increase the resources if you want to keep performance unchanged?
## Maintainability
Maintainability has many facets, but in essence it’s about making life better for the engineering and operations teams who need to work with the system.

Good abstractions can help reduce complexity and make the system easier to modify and adapt for new use cases. 

Good operability means having good visibility into the system’s health, and having effective ways of managing it.

# Data Models and Query Languages
## Graph-Like Data Models
Graph-like data models shine when there are many many-to-many relationships in your data. 

Graphs can represent both homogenous and heterogenous data. 

For example, Facebook maintains a single graph with many types of vertices and edges: vertices represent people, locations, events, checkins, and comments made by users; edges indicate which people are friends with each other, which checkin happened in which location, who commented on which post, who attended which event, and so on.

## Property Graphs
In the property graph model, each vertex consists of: 
- A unique identifier

- A set of outgoing edges

- A set of incoming edges

- A collection of properties (key-value pairs)

Each edge consists of:
- A unique identifier

- The vertex at which the edge starts (the tail vertex)

- The vertex at which the edge ends (the head vertex)

- A label to describe the kind of relationship between the two vertices

- A collection of properties (key-value pairs)

### Property Graph Represented as a Relational Schema
You can think of a graph store as consisting of two relational tables, one for vertices and one for edges
```
CREATE TABLE vertices (
    vertex_id   integer PRIMARY KEY,
    properties  json
);

CREATE TABLE edges (
    edge_id     integer PRIMARY KEY,
    tail_vertex integer REFERENCES vertices (vertex_id),
    head_vertex integer REFERENCES vertices (vertex_id),
    label       text,
    properties  json
);

CREATE INDEX edges_tails ON edges (tail_vertex);
CREATE INDEX edges_heads ON edges (head_vertex);
```
The head and tail vertex are stored for each edge; if you want the set of incoming or outgoing edges for a vertex, you can query the edges table by head_vertex or tail_vertex, respectively.

### Important Aspects of the Property Graph Model
1. Any vertex can have an edge connecting it with any other vertex. There is no schema that restricts which kinds of things can or cannot be associated.

2. Given any vertex, you can efficiently find both its incoming and its outgoing edges, and thus traverse the graph—i.e., follow a path through a chain of vertices—both forward and backward.

3. By using different labels for different kinds of relationships, you can store several different kinds of information in a single graph, while still maintaining a clean data model.

## Triple Stores
The Triple-store model is mostly equivalent to the property graph model, using different words to describe the same ideas.

In a triple-store, all information is stored in the form of very simple three-part statements: (subject, predicate, object). For example, in the triple (Jim, likes, bananas), Jim is the subject, likes is the predicate (verb), and bananas is the object. 

The subject of a triple is equivalent to a vertex in a graph. The object is one of two things: 

1. A value in a primitive datatype, such as a string or a number. In that case, the predicate and object of the triple are equivalent to the key and value of a property on the subject vertex. For example, (lucy, age, 33) is like a vertex lucy with properties {"age":33}.

2. Another vertex in the graph. In that case, the predicate is an edge in the graph, the subject is the tail vertex, and the object is the head vertex. For example, in (lucy, marriedTo, alain) the subject and object lucy and alain are both vertices, and the predicate marriedTo is the label of the edge that connects them.