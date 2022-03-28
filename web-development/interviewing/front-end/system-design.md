---
title: System Design Questions
description: 
published: true
date: 2022-03-28T23:29:40.788Z
tags: interviewing, front-end
editor: markdown
---

# Overview
## Step 1: Requirements clarifications and alignment
- What devices should the system support? Desktop web, mobile web, etc.
- What's the primary device that users will access the system on?
- Which browsers should we support?
- Do we need to support internationalization?
- How much styling customization do we want to allow?

### Example: Designing Twitter
- Will users of our service be able to post tweets and follow other people?
- Should we also design to create and display the user’s timeline?
- Will tweets contain photos and videos?
- Are we focusing on the backend only, or are we developing the front-end too?
- Will users be able to search tweets?
- Do we need to display hot trending topics?
- Will there be any push notification for new (or important) tweets?

## Step 2: Back-of-the-envelope-estimation
Always a good idea to estimate the scale of the system we're going to esign. This will help later when we focus on scaling, partitioning, load balancing, and caching. 
### Example: Designing Twitter
- What scale is expected from the system? (number of new tweets, number of tweet views, number of timeline generations per second)
- How much storage will we need? We will have different requirements if users can have photos and videos in their tweets.
- What network bandwidth usage are we expecting? This will be crucial in deciding how we will manage traffic and balance load between servers.
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
#### Lazy loading
#### Preloading / Prefetching data ahead of time
### Accessibility
- Make sure there is correct color contrast for colorblind or sight impaired users.
- Use the right HTML tags for semanticness, or the right `aria-role` attributes.
- Clickable items should have the correct cursor style to indicate they can be clicked.
- Images should have `alt` text. Go through your app with a screen reader.
### I18N
- Never concatenate localized strings ( word order is diff between languages)
- Handle different content sizes
- Be aware of cultural signifigance of colors
### Security