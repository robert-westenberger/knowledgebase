---
title: Front End HTML Interview Questions
description: 
published: true
date: 2022-03-25T14:16:11.841Z
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
Set on the client or by the server. The server can use the `Set-Cookie` header. It's possible to persist across browser sessions depending on whether the expiration on it is set. Cookies are automatically set with every request using the `Cookie` header. 
## sessionStorage
Set on the client. It lasts until the tab of the site for which it's set is closed.
## localStorage
Set on the client. It lasts until cleared, and is persistent across browser sessions and is accessible from any window. It stays on the client.

# Describe the difference between `<script>`, `<script async>`, and `<script defer>`
-`<script>` HTML parsing is blocked, the script is fetched and executed immediately, HTML parsing resumes after the script is executed. 
-`<script async>` - The script will be fetched in parallel to HTML parsing and executed as soon as its available, potentially before HTML parsing is complete. Use `async` when the script is independent of any other scripts on the page, for example, analytics. 
-`<script defer>`- The script will be fetched in parallel to HTML parsing and executed when the page has finished parsing. If there are multiple of them, each deferred script is executed in the order they were encountered in the document. If a script relies on a fully-parsed DOM, the defer attribute will be useful in ensuring that the HTML is fully parsed before executing.

# Why is it a generally good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
## Links in the `<head>` 
This is part of proper specification in building an optimized website. When a page first loads, HTML and CSS are being parsed simultaneously; HTML creates the DOM and CSS creates the CSSOM. Both are needed to allow for a quick "first meaningful paint" timing. 

Placement of script tags near the bottom of the body tag might cause flashes of unstyled content (FOUC).

## Scripts just before `</body>`
`<script>` tags block HTML parsing while they are being downloaded and execute which can slow down your page. Placing scripts at the bottom will allow the HTML to be parsed and displayed to the user first.

An exception for positioning of `<script>`s at the bottom is when your script contains `document.write()`, but using `document.write()` is not good practice. Also, placing `<script>`s at the bottom means that the browser cannot start downloading the scripts until the entire document is parsed. This ensures that your code that needs to manipulate DOM elements will not throw an error and halt the entire script. 

If you need to put `<script>`s in the head, use the defer attribute, which will only execute the scripts once the DOM is loaded, but it will fetch them all in parallel. 

# What is progressive rendering?
Techniques to improve performance of a webpage (improving perceived load time).

## Examples
### Lazy loading of images
Javascript will be used to load an image when the user scrolls into the part of the page that displays that image
### Prioritizing visible content 
AKA above the fold rendering. Includes only the minimum CSS/content/scripts necessary for the amount of page that would be rendered in the users browser first to display as quickly as possible.

# Why would you use a `srcset` attriute in an image tag? Explain the process the browser uses when evaluating the content of this attribute
This allows you to serve different images for different screen resolutions. 