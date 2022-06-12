---
title: Data Intensive Applications
description: 
published: true
date: 2022-06-12T02:34:54.706Z
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
Historically, data started out being represented as one big tree (the hierarchical model), but that wasn't good for representing many-to-many relationships, so the relational model was invented to solve that problem. 

More recently, "NoSQL" datastores have emerged and are of two main types: 

1. **Document databases** - targets use cases where data comes in self-contained documents and relationships between one document and another are rare.

2. **Graph databases** - targets use cases where anything is potentially related to everything. 

One thing that document and graph databases have in common is that they typically don’t enforce a schema for the data they store, which can make it easier to adapt applications to changing requirements. However, your application most likely still assumes that data has a certain structure; it’s just a question of whether the schema is explicit (enforced on write) or implicit (assumed on read).


## MapReduce Querying
Based on the map / collect and reduce / fold / inject functions that exist in many functional programming languages.

The map and reduce functions used in MapReduce must be pure. They can't perform additional queries, and must be free of any side effects.

These restrictions allow the database to run the functions anywhere, in any order, and rerun them on failure. 

MapReduce is a fairly low level programming model for distributed execution on a cluster of machines.
### Example
Imagine you are a marine biologist, and you add an observation record to your database every time you see animals in the ocean. Now you want to generate a report saying how many sharks you have sighted per month.

#### Using PostgreSQL
In PostgreSQL, the query would look like the following:

```
SELECT date_trunc('month', observation_timestamp) AS observation_month,
       sum(num_animals) AS total_animals
FROM observations
WHERE family = 'Sharks'
GROUP BY observation_month;
```

This query first filters the observations to only show species in the `Sharks` family, then groups the observations by the calendar month in which they occurred, and finally adds up the number of animals seen in all observations in that month.

#### Using Mongodb's MapReduce
The same can be expressed with MongoDB's MapReduce feature as follows:

```
db.observations.mapReduce(
    function map() { 
        var year  = this.observationTimestamp.getFullYear();
        var month = this.observationTimestamp.getMonth() + 1;
        emit(year + "-" + month, this.numAnimals); 
    },
    function reduce(key, values) { 
        return Array.sum(values); 
    },
    {
        query: { family: "Sharks" }, 
        out: "monthlySharkReport" 
    }
);
```
The javascript `map` function is called once for every document that matches `query`, with `this` set to the document object.

The `map` function emits a key ( a string consisting of year and month, such as `"2013-12"` or `"2014-1"`) and a value (the number of animals in that observation).

The key-value pair emmited by `map` are grouped by key. For all k-v pairs with the same key (i.e., the same month and year), the `reduce` function is called once.

The `reduce` function adds up the number of animals from all observations in a particular month. 

The final output is written to the collection `monthlySharkReport`. 

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

# Storage and Retrieval
## Data Structures That Power Your Database
An `index`, in a general sense, is a data structure that maintains some additional metadata derived from the primary data in the database. The index is used as a "signpost" to help locate data during searches. 

Maintaining additional structures incurs overhead, especially on writes, because the index needs to be updated to account for the new data. 

### Hash Indexes
Key-value stores are usually implemented as a hash map / hash table. 

If we were using a dead simple database, such as just appending new entries to a big text file, then a hash index for our data would be an in-memory hash map where every key is mapped to a byte offset in the data file - the value at which the value can be found. 

#### Disadvantages
- The hash table must fit in memory, so if you have a very large number of keys, you’re out of luck. In principle, you could maintain a hash map on disk, but unfortunately it is difficult to make an on-disk hash map perform well. It requires a lot of random access I/O, it is expensive to grow when it becomes full, and hash collisions require fiddly logic

- Range queries are not efficient. For example, you cannot easily scan over all keys between `kitty00000` and `kitty99999`—you’d have to look up each key individually in the hash maps.

### SSTables (Sorted String Tables) and LSM-Trees (Log-Structured Merge-Tree)
SSTables are like hash indexes, but they key-value pairs are **sorted by key**.

#### Advantages Over Log Segments With Hash Indexes
1. Merging segments is simple and efficient, even if the files are bigger than the available memory. You start reading the input files side by side,look at the first key in each file, copy the lowest key (according to the sort order) to the output file, and repeat. This produces a new merged segment file, also sorted by key. 

2. In order to find a particular key in the file, you no longer need to keep an index of all the keys in memory. Say you're looking for they key `handiwork`, but you don't know the exact offset of that key in the segment file. However, say you know the offsets for keys `handbag` and `handsome`, and because of the sort order you know that `handiwork` must appear between these two. This means you can jump to the offset for `handbag` and scan from there until yo¨find `handiwork` (or not, if it's not in that file). 
You still need an in-memory index to tell you the offsets for some of the keys, but it can be sparse: one key for evry few kbs of segment file is sufficient, because a few kilobytes can be scanned very quickly.
3. Since read requests need to scan over several key-value pairs in the requested range anyway, it is possible to group those records into a block and compress it before writing it to disk.  Each entry of the sparse in-memory index then points at the start of a compressed block. Besides saving disk space, compression also reduces the I/O bandwidth use.

#### Constructing and Maintaining SSTables
You can use red-black trees, or AVL trees, to insert keys in any order and read them back in sorted order.

- When a write comes in, add it to an in-memory balanced tree data structure (sometimes called a memtable). 

- When the memtable gets bigger than some threshhold, typically a few megabytes, write it out to disk as an SSTable file. This can be done efficiently because the tree already maintains the key-value pairs sorted by key. The new SSTable file becomes the most recent segment of the database. While the SSTable is being written out to disk, writes can continue to a new memtable instance.

- In order to serve a read request, first try to find the key in the memtable, then in the most recent on-disk segment, then in the next-older segment, etc.

- From time to time, run a merging and compaction process in the background to combine segment files and to discard overwritten or deleted values.

This process suffers from one problem: if the database crashes, the most recent writes (which are in the memtable but not yet written out to disk) are lost. 

In order to avoid that problem, we can keep a separate log on disk to which every write is immediately appended, just like in the previous section. That log is not in sorted order, but that doesn’t matter, because its only purpose is to restore the memtable after a crash. Every time the memtable is written out to an SSTable, the corresponding log can be discarded.

#### Performance Optimizations
The LSM-tree algorithm can be slow when looking up keys that don't exist in the db. You have to check the memtable, then the segments all the way back to the oldest (possible having to read from disk for each one) before you can be sure the key does not exist. 

In order to optimize this kind of access, storage engines often use additional Bloom filters (a memory-efficient data structure for approximating the contents of a set. It can tell you if a key does not appear in the database, and thus saves many unnecessary disk reads for nonexistent keys).

There are also different strategies to determine the order and timing of how SSTables are compacted and merged. The most common options are size-tiered and leveled compaction. LevelDB and RocksDB use leveled compaction (hence the name of LevelDB), HBase uses size-tiered, and Cassandra supports both. In size-tiered compaction, newer and smaller SSTables are successively merged into older and larger SSTables. In leveled compaction, the key range is split up into smaller SSTables and older data is moved into separate “levels,” which allows the compaction to proceed more incrementally and use less disk space.

The basic idea of LSM-trees - keeping a cascade of SSTables that are merged in the background- is simple and effective. 

### B-Trees
B-Trees are the most widely used indexing structure for relational databases (and many nonrelational databases).

B-trees break down the database into fixed-size blocks or pages, traditionally 4 KB in size, and read or write one page at a time. This design corresponds more closely to the underlying hardware. 



