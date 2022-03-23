---
title: Behavioral Questions
description: 
published: true
date: 2022-03-23T22:29:34.721Z
tags: interviewing
editor: markdown
---

# Accomplishments that can be used
## Magic Responsive Tables
### Situation
We were making all of screens in our app responsive. A large portion of our app were still legacy coldfusion, and there were still a lot of layout and data tables in use that were prohibitively difficult to make responsive. 

This had to be completed as quickly as possible, and was going to take a lot of resources away from the UI team. 
### Task 
The task was to refactor all of the layout tables to be more responsive and themeable markup and styling. 
### Action
I made a relatively small (500-600 line) script that would parse these tables for their actual table or other useable markup, and then inject into the DOM more modern markup from a template. It would execute on page load, and under a certain viewport width it would hide the original table and show the updated markup. 
### Result 
This allowed us to to sidestep the issue of having to refactor nearly 100 legacy coldfusion tables. This was an acceptable stopgap to get everything completely responsive while we work on actually refactoring those screens to actual react apps.
## Introducing Strict Linting to our FE build
### Situation
We were running into issues where code would be commited to a release, would be deployed, and it would entirely break the shell of the site because there was a missing import or some other issue. The build process wouldn't complete, but it still contained problematic code that wouldn't cause issues until runtime. This would result in a critical escalation, all hands on deck to identify and fix the issue. (In reality, it would only take one person a little bit to actually find and fix the issue.. but they would have to pull down the latest code and do a build locally
### Task 
Had to preven this situation from cropping up again. 
# List of common behavioral questions
## Tell me about a time when you were faced with a challenging situation. How did you solve it?
## Do you usually set goals at work? If yes, could you give me an example of a goal you had and how you achieved it?
## Give me an example of a time you made a mistake at work. 
## Have you ever faced conflict with a coworker? How did you resolve the situation?
## Tell me about a time when you handled pressure well.
## Was there a time when you had to be very strategic in order to meet a goal?
## Give me an example of a situation when you showed initiative and took charge of a situation.
## Tell me about a time when you went above and beyond your duties for a job or task.
## Did you ever have to correct one of your superiors when they were wrong? How did you approach that situation?
## Have you ever had to work under a tight deadline?
## How do you deal with coworkers that don't cooperate or can't contribute enough? 
## Tell me about a time when a client was asking for the impossible. How did you explain and communicate this to them?
## Give me an example of a time when you didn’t meet a client’s expectations. How did you deal with the situation?
## Is there a situation you think you could’ve handled better or differently?
## How do you adapt to sudden changes in the workplace? Could you give me an example?
## Tell me about a time when you had to think on your feet in order to deal with a situation.
## Sometimes employers put too much on their employees’ plates. Was there a time when you were overwhelmed with work? How did you handle the situation?
## Tell me about a time when you had the liberty to be creative with your work. Was it exciting or difficult for you?
## Give me an example of a time when you and your team had opposing views on an issue. How did you persuade them to go with your decision?