---
title: Front End HTML Interview Questions
description: 
published: true
date: 2022-03-25T01:35:41.196Z
tags: interviewing
editor: markdown
---

# What does a DOCTYPE do?
DOCTYPE is an abbreviation for Document Type. A DOCTYPE is always associated to a DTD - for Document Type Definition. 

For webpages, the DOCTYPE declaration is required. It is used to tell user agents what version of the HTML specifications your document respects. Once a user agent has recognized a correct DOCTYPE, it will trigger the no-quirks mode matching this DOCTYPE for reading the document. If a user agent doesn't recognize a correct DOCTYPE, it will trigger the quirks mode.

The DOCTYPE declaration for the HTML5 standards is `<!DOCTYPE html>`.

# How do you serve a page with content in multiple languages?
When an HTTP request is made to a server, the requesting user agent usually sends information about language preferences, such as the `Accept-Language` header. The server can then use this information to return a version of the document in the appropriate language if such an alternative is available. The returned HTML document should declare the `lang` attribute in the `<html>` tag, like `<html lang="en">...</html>`

To let a search engine know that the same content is available in different languages, you must also make use of the `hreflang` attribute in the `<head>`. Something like `<link rel="alternate" hreflang="de" href="http://de.example.com/page.html" />`. 

# What kind of things must you be wary of when designing or developing for multilingual sites?
- Use `lang` attribute in your HTML.
- Direct users to their native language. IT should be easy to change his country/language easily.
- Text in png, gif, jpg etc is not scalable. 
- Be wary of text length. Some content can be longer in other languages, creating layout issues.
- Be mindful of how colors are perceived across cultures.
- Formatting of dates and currencies. 
- Don't concatenate translated strings. Languages will have different word order.
- Language reading direction (LTR vs RTL).

# What are data- attribute good for?
They are intended to store extra data within DOM nodes. They generally aren't encouraged anymore since the data model is better stored within javascript itself. 

# Describe the difference between a `cookie`, `sessionStorage`, and `localStorage`
All of them are key-value storage mechanisms on the client side. They are only able to store values as strings.
## cookie

## sessionStorage
## localStorage