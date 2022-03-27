---
title: Behavioral Questions
description: 
published: true
date: 2022-03-27T20:45:57.029Z
tags: interviewing
editor: markdown
---

# Accomplishments that can be used
## Transcoding Service
I was tasked with creating a service that would detect encoding type, and based off of that encoding type, transcode and compress a video for use on the web. 

For that, I used ffmpeg, and simple message service to send a message to the encoding server once transcoding was complete. 

Multiple problems did occur. Sometimes, videos weren't actually transcoded correctly. Other times, the message that transcription actually completed were never sent. 

Then, because there  were problems, we pivoted to using Amazon ElasticTranscoder and Amazon Simple Message Service for the transcoding pipeline. Eventually, we got the system working, but it exceeded both time anad budget. 

In retrospect, we could have just uploaded everything to youtube. 
### Situation
I was working on a whitelabel online learning platform. Platform provided the option for users to upload images and video. In order for the content that users uploaded to be useable, it needed to be transcoded. 
### Task
To make a concurrently available transcoding service that is both reliable and performant. 
### Action
- I made an encoding detector in python. 
- I used ffmpeg and python to actually transcode the video, depending on the videos current encoding. 
- I used SMS to send a message from the encoding server to the web server once encoding was complete, to indicate that the video is now useable. 
- There were problems with the encoding service. It needed to be load balanced, and we needed to support different encodings for different devices.
- After recognizing those issues, I pivoted to using AWS and their transcoding and SMS pipelines. 
### Result 
I delivered the product, following constraints and requirements, over time and over budget. 


### What did I learn
Instead of tackling the problem right away, think about all available options. 

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
### Action
Introduce linting to the front end build that would run on production builds. Any lint errors would fail the pipeline and prevent code from being merged into a release branch. 

We actually had to do this in a few phases, setting only the most important linting rules to error out at first since our codebase had so many linting issues. Once we had ESlint setup however, there was a clear path from no-linting -> strict linting that we completed in a few months. I remember we used some react code mod tools to refactor some of our react code.
### Result
Less deploy issues that needed the attention of the entire UI team. Also general improvement of codebase... there was now static analysis of any issues and there was also a more standardized coding style that was programatically enforceable.

## Create small node based FTP tool for easier content modifications
### Situation
Our platform has a "content system", where clients can upload html markup, scripts, assets, web forms, etc. to be used on any screen of the app or even create their own pages. Uploading content assets was a particular pain in the ass, because you had to click through this legacy system for each content asset, and upload assets individually. 

The idea was to upload these assets, and then the clients could modify them on their own time without developer intervention or a code deploy. 
### Task
This was on my own initiative, and was driven mainly out of frustration from using the old system. It was a nightmare to upload anything more than 5 assets at a time. 
### Action
Made a small node app that just authenticated and FTPd content assets to the appropriate directory on the server. Many more files could be Created, read, updated, and deleted at once than what the web interface could do.
### Result
Implementation speed and ease took a lot faster. 

## Design system 

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