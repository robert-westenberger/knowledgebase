---
title: System Design Questions
description: 
published: true
date: 2022-03-26T19:16:46.813Z
tags: interviewing, front-end
editor: markdown
---

# Overview
## Requirements clarifications and alignment
- What devices should the system support? Desktop web, mobile web, etc.
- What's the primary device that users will access the system on?
- Which browsers should we support?
- Do we need to support internationalization?
- How much styling customization do we want to allow?
## Architecture
List down various subcomponents that will exist within components of the architecture. 

Detail what data is being passed down among each component. It may be helpful to draw diagrams to illustrate the entities and their relationships.
## Data Model Design
- State should be consolidated at the top level. 
- There should be as little state as possible. If something can be derived, it should live outside the state itself.
## API Design
### What are the configuration options you would allow for the component?
### Follow Open-Closed Principle
The component should be open for extension but closed for modification.

In other words, when extending functionality of our program, we should be able to just add functionality to our base object / class, rather than adding (modifying) the behavior to the base class or object.
## Extra Stuff
### Multi device support
### User Experience
### Performance
### Accessibility
### I18N
### Security