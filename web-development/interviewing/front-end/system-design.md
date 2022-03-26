---
title: System Design Questions
description: 
published: true
date: 2022-03-26T19:21:10.147Z
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
### If the component is a part of a UI library, then the user should be allowed to customize the look and feel of the components
### Add event handlers if necessary 
## Extra Stuff
### Multi device support
### User Experience
#### Reflect state of the component to the user
- Loading animations. 
- Display error messages to user if appropriate.
#### Display empty state if there are no items in a list
#### Destructive actions, like delete, should have a confirmation step
#### Disable interactive elements if they trigger an async request
#### If there are search inputs involved, each keystroke should not fire a network request
#### Handle extreme cases
- Make sure UI works, if internationalized
- If there are many items in a component, perhaps paginate them
### Performance

### Accessibility
### I18N
### Security