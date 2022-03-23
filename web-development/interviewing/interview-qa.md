---
title: Interviewing QA
description: 
published: true
date: 2022-03-23T16:00:05.307Z
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

REST based services follow some of the above principles but not all. RESTful services means it follows all of the above principles.
### Websocket vs REST
1. Websocket is a low-level protocol based on the concept of a socket and port, which are the underlying transport mechanism.. whereas REST is based on CRUD.
2. WebSocket requires IP address and Port details, which are lower level details. RESTful application needs to design operation based on HTTP verbs and is HTTP based.
3. Websockets are bidirectional in nature, REST is unidirecitonal.
4. WebSockets are ideal for real time scalable applications, where REST is for high request volume.
5. WebSocket is stateful. 
6. Websockets work better where the client server communicates over the same TCP connection for the life of the websocket connectionm whereas for an HTTP request, a new TCP connection is initiated.
### What's the difference between PUT and POST?
POSTs will create a resource, and PUT updates a resource. PUTs are idempotent, so making the same PUT request multiple times will have the same effect as calling it once. Making multiple POST requests will create resources multiple times.
### What are the best practices to create a standard URI for a web service?
- A resource can be a singleton or a collection. For example, `/customers` can identify multiple customers, and `/customers/{customerId}` can identify a single customer.
- A resource may contain a sub-collection of resources. `/customers/{customerId}/accounts` will identify the accounts of a particular customer. `/customers/{customerId}/accounts/{accountId}` will identify a particular account.
- RESTful URI should refer to resources that are nouns, and not HTTP verbs.
- Use forward slash to denote hierarchical relationships.
- Don't use trailing forward slash in URIs.
- Use hyphens, not underscores, to imrpove readability.
- Allow query parameters to filter URI collection.
### What are the four resource archetypes in a RESTful architecture?
- **Document**: Akin to an object instance or database record. In REST, its a single resource inside a resource collection. A document's state representation typically includes both fields with values and links to other related resources. These should be singular.
```
https://api.example.com/device-management/managed-devices/{device-id}
https://api.example.com/user-management/users/{id}
https://api.example.com/user-management/users/admin
```
- **Collection**: Server managed directory of resources. Clients may propose new resources be added to a collection, however its up to the collection resource to choose to create a new resource or not. These should be plural.
```
https://api.example.com/device-management/managed-devices
https://api.example.com/user-management/users
https://api.example.com/user-management/users/{id}/accounts
```
- **Store**: A store is a client-managed resource repository. A store resource lets an API client put resources in, get them out, and decide when to delete them. A store never generates new URIs. Instead, each stored resource has a URI. The URI was chosen by a client when the resource was initially put into the store. These should be plural.
```
https://api.example.com/song-management/users/{id}/playlists
```
- **Controller**: A controller resource models a procedural concept. They are like executable functions, with parameters and return values, inputs and outputs. Use "verb" to denote contorller archetype.
```
https://api.example.com/cart-management/users/{id}/cart/checkout 
https://api.example.com/song-management/users/{id}/playlist/play
```
### What is the use of Accept and Content-Type Headers in HTTP Requests?
The Accept HTTP header indicates which content types, expressed as MIME types,the client is able to understand. The server uses content negotation to select one of the proposals and informs the client of the choice with the Content-Type response header. 

Content-type can be used both by client and server to identify the format of the data in their request(client) or response(server), and therefore, help the other part interpret the information correctly.
### What is statelessness in RESTful web services?
A restful web service shouldn't keep client state on the server. With each request, its the responsibility of the client to pass its context to the server and then the server can store this context to process the client's further request. 

Advantages are: 
- Web services can treat each method request independently.
- Since HTTP is stateless, RESTful web services work seamlessly with HTTP protocols.

Disadvantages:
- Web services need to get extra information in each request and then interpret to get the client's state in case the client interactions are to be taken care of.

### What are the best practices for caching?
### What are different ways to test web services?
### What are the best practices to design a resource representation?
### What is the purpose of HTTP Status Code?
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
