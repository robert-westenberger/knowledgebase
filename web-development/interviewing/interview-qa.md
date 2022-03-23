---
title: Interviewing QA
description: 
published: true
date: 2022-03-23T14:44:45.301Z
tags: interviewing
editor: markdown
---

# Frontend
## Testing
### What is Jest/Enzyme used for?
### What is snapshot testing?
## React
### What is batching in react?
React will group multiple state updates in a single rerender under the hood as a performance optimizations.
### What are higher order components?
### Benefits of class over function components?
### When would you use a class or function component?
## Typescript
### What are the pros and cons of working with typescript?
## Javascript
### What is hoisting?
### What's the difference between a normal function declaration and an arrow function?


# Backend
## SQL
### What are the pros and cons of holding domain logic in stored procedures?
## Software Engineering
### Singleton is a design pattern that restricts the instantiation of a class to a single object. Writing a Thread-Safe Singleton class is not so obvious. Would you try?
### The ability to change implementation without affecting clients is called Data Abstraction. Produce an example violating this property, then fix it. 
### What are generics?
## Web Architecture
### Explain the difference between a cookie and a session
## API Design
### What are the core components of an HTTP Request?
It has five major parts
- **Verb** GET, POST, DELETE, PUT, etc
- **URI** Uniform Resource Identifier to identify the resource on the server
- **HTTP Version** HTTP version, like HTTP v1.1
- **Request Header** Contains metadata for the HTTP request message as kv pairs. For example, client or browser type, format supported by client, format of message body, cache settings, etc. 
- **Request Body** Message content or resource representation
### What are the advantages of REST web services?
- Easy learning curve, works on HTTP protocol.
- Supports multiple technologies for data transfer such as text, xml, json, image, etc.
- No contract defined between server and client, loosely coupled implementation.
- Easily testable over the browser. 
### Mention some key characteristics of REST
- REST is stateless, therefore the server has no state or session data
- Web services use POST calls to make operations and GET to access resources.
### What is a cached response? 
- Caching refers to storing server response in client itself so that a client needs not to make a server request to the same resource again and again. A server response should have information about how a caching is to be done so that a client caches a response for a period of time or never caches the server response.
### What are the different types of Web Services?
Two types of web services
- **SOAP Web Services** Runs on the SOAP protocol and uses XML tech for sending data.
- **RESTful Web Services**: Architectural style that runs on HTTP/HTTPS protocol. Its a stateless client-server architecture where web services are resources and can be identified by their URIs. 
### What are resources in a REST arhitecture?
Identified by logical URLs, these are the things accessed by the URL you supply. In a book API, one resource might be `example.com/api/v1/books`, where a GET request will return an array of either one or multiple books depending on the request configuration. A POST to `example.com/api/v1/books/32/` will update whatever book with an ID of 32 (just an example, there is no enforced API design in REST.
### What are the advantages of Web Services?
- **Interoperability**: Server can be one language, client in another. There is a common protocol used for transporting data.
- **Reusability**: One web service can be reused by many client applications.
- **Multiple Service Versions** can be running at the same time.

### Whats the difference between REST and RESTful?
REST is an architectural style of development that is:
- stateless and sessionless
- has access to all the resources from the server using only URI
- does not have built in encryption
- uses only the HTTP protocol
- for performing CRUD operations, it should use GET POST PUT and DELETE
- should return the result in the form of JSON, XML

REST based services follow some of the above principles but not all. RESTful services means it follows all of the above principoles.
## Design Patterns
### Inversion of Control
#### What is inversion of control, and how does it improve the design of code?
### Active-Mapper
#### What is the Active-Record design pattern? What are the limits and pitfalls of this pattern?
### Data-Mapper
#### What is the Data-Mapper design pattern? When would you use Active-Mapper vs Data-Mapper?

# Fullstack
## Architecture
### How would you handle large data sets from the backend to the frontend?
## Software Engineering
### Explain the difference between classical and prototypal inheritance
### Many state that, in OOP, composition is often a better option than inheritance. What's your opinion?
### How would you go about clearing tech debt?
### How would you deal with dependency hell?
### It is said that one of the most important goals in OO design is to have high cohesion and loose coupling. What does it mean? Why is it important and how is it achieved?
### In your opinion, why has OOP dominated the market for so many years?
### What does it mean when a language treats functions as first-class citizens? Why is it important that in a language functions are first-class citizens?
## Testing
### What is your approach to testing?
## Functional Programming
### What are higher order functions?
# Other
## Workflow
### Whats your product release cycle like?
### Do you do sprints?
