---
title: Project Ideas / Career
description: 
published: true
date: 2020-12-19T00:58:43.136Z
tags: 
editor: markdown
---

# Projects
## Learning Experiences


### TTF renderer
### GIF or JPEG en/decoder
### Video decoder (start with H.261)
### Text Editor
Things to learn:

Data structures for storing the text: array, rope, gap buffer, piece table.
Behavior and implementation of the text cursor.
Design patterns for undo/redo: memento, command.
Abstractions to separate the visual and memory aspects of the text.

### Compiler - Tiny BASIC
Things to learn:

Lexical analysis
Syntactic analysis
Recursive descent parsing
Abstract syntax tree
Semantic analysis
Optimization passes
Code generation

### Mini Operating System
Things to learn:

Cross compiling
Bootloading
BIOS interrupts
x86 modes
Memory management and paging
Scheduling (e.g., round robin)
File systems (e.g., FAT)

### Database
Write a database. Depending on what angle you take, it can look like a compiler (SQL parsing, predicate evaluation, optimizing for index usage), OS (file systems for in-place updates of complex data structures, and scheduling with lock dependencies), distributed systems (consistency and availability tradeoffs across machines, with possible partitions).
And then there's the whole mental model of relational algebra and stream processing of queries.

### 3D renderer

### Shell

### Git

### Virtual Machine / Game emulator


# Career

### On learning deeply
1. Pick a data structure (such as a hash table or LSM-Tree) then read all the literature there is to read, every single paper that's great, following the best conferences year after year, and implement a 10x faster or more scalable version for the std lib of your favorite language.

2. Pick a fault model (such as storage faults, network faults, cryptography faults) then read all the literature there is to read, every single paper that's great, following the best conferences year after year, and write a fault injection or fuzzing harness to break some of the most respected storage/network/cryptography systems (for examples, see the work done by Remzi and Andrea Arpaci-Dusseau on storage faults, Kyle Kingsbury on Jepsen, and Guido Vranken on Cryptofuzz: https://github.com/guidovranken/cryptofuzz).

3. Pick a software field (such as web applications, mobile applications, native applications, file formats such as Office Open XML, or protocols such as SMTP, MIME, HTTP, QUIC) then read as many CVE reports and bug bounty reports as you can find, and then start participating in bug bounty programs within this field. Pick a target and give yourself a goal, e.g. DoS, RCE or read/write access, and do the work to make it happen. Chain as many steps as you can. Automate and enumerate. You'll find a way in if you keep at it. There's nothing like crafting an exploit to change the way you think about programming.

As you gain experience in data structures, storage/networking/cryptography, and security, you'll find this translates well to most software engineering work. You'll gain a speed/safety/security way of thinking, you'll have fun being curious and learning along the way (and hopefully you'll earn a bounty or two and get some CVEs under your name).


> Let’s say I’ve picked a data structure. How would you suggest identifying the great papers and best conferences related to it?

1. Add "abstract" to your search query to surface papers.

2. Search for "... reading list". For example, Heidi Howard maintains https://github.com/heidihoward/distributed-consensus-reading...

3. Read blogs like "The Morning Paper" (https://blog.acolyer.org) but skip fields that are outside your scope. You don't have time to follow more than one or two (or three) major fields.

4. Use Google Scholar to find the most cited papers, or to find papers that build on papers you think are good.

5. Keep an eye out for the conferences where these papers were presented. Then read the other papers that were also presented.

6. When you come across an amazing paper, read other papers by the same authors or supervisors.

7. If you're lucky you might also find good "survey" papers that cover and reference the state of the art.

8. Lecture notes from Stanford or MIT or another university can also be a great way to get a big picture of the evolution of techniques for a given data structure or problem. For example, these lecture notes are just brilliant for getting started with stuff around memory hierarchies: https://www.eidos.ic.i.u-tokyo.ac.jp/~tau/lecture/parallel_d...

