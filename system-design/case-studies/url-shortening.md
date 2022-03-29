---
title: URL Shortening Service
description: 
published: true
date: 2022-03-29T16:42:33.190Z
tags: interviewing, system-design
editor: markdown
---

# Why do we need URL shortening?
Short links that redirect to longer URLs are useful because they 
- Save a lot of space when displayed, printed, messaged, or tweeted. 
- Optimize links across devices
- Track individual links to analyze audience, measure ad campaign's performance
- Hide affiliated URLs

# Requirements
## Functional Requirements
1. Given a URL, our service should generate a shorter and unique alias of it. It sohuld be short enough to be easily copied and pasted into applications.
2. When users access a short link, our service should redirect them to the original link.
3. Users should optionally be able to pick a custom short link for their URL.
4. Links will expire after a standard default timespan. Users should be able to specify the expiration time.

## Nonfunctional requirements
1. It should be highly available. If our service is down, all the URL redirections will start failing.
2. Redirection should happen in real time with minimal latency.
3. Shortened links should not be guessable/predictable.

## Extended requirements
1. Analytics (how many times a redirection happened?)
2. Should be accessible through REST APIs by other services.

# Capacity Estimation and Constraints
The system will be read-heavy. There will be lots of redirection requests compared to new URL shortenings. 

We can assume a 100:1 ratio between read and write.

## Traffic Estimates
Assuming we have 500m new URL shortenings per month, we can expect 50b redirections in the same period. 

### Queries Per Second
500m / (30 days * 24 hours * 3600 seconds) = ~200 new URLs / second

Considering a 100:1 read/write ratio, redirections would be 20,000 per second.

## Storage Estimates
Assume we store every URL shortening request for 5 years. Since we expect 500M new URLS every month..

500 million * 5 years * 12 months = 30 billion 

Assuming every stored object is 500 bytes (ballpark estimate), we need

30 billion * 500 bytes = 15TB.

## Bandwidth Estimates
### Write requests
200 new URLs every second, at 500 bytes each
200 * 500 bytes = 100 KB/s

### Read requests
20,000 redirects per second, at 500 bytes each
20,000 * 500 = 10 MB/s

## Memory estimates
If we want to cache some hot URLs that are frequently accessed, how much memory will we need?

If we follow the 80-20 rule, meaning 20% of URLs generate 80% of traffic, we would like to cache 20% hot URLs. 

With 20K requests per second, we will be getting 1.7 billion requests per day. 

To cache 20% of those requests, we will need 170 GB of memory. 

0.2 * 1.7 bilion * 500 bytes = 170GB

Note that, since there will be many duplicate requests of the same URL, actual memory usage will be less than 170GB.

# System APIs
## Creating and deleting URLs
### Creating URLs
```
createURL(api_dev_key, original_url, custom_alias=None, user_name=None, expire_date=None)
```
**Parameters:**
api_dev_key (string): The API developer key of a registered account. This will be used to, among other things, throttle users based on their allocated quota.
original_url (string): Original URL to be shortened.
custom_alias (string): Optional custom key for the URL.
user_name (string): Optional user name to be used in the encoding.
expire_date (string): Optional expiration date for the shortened URL.

**Return*:
A successful insert returns the shortened URL; otherwise, it returns an error code.

### Deleting URLs
```
deleteURL(api_dev_key, url_key);
```
url_key is a string representing the shortened URL to be retrieved; a successful deletion returns 'URL Removed'.

## Preventing Abuse
We can limit users via their api_dev_key, so a malicious user can't consume all URL keys. 

# Database Design
A few observations about the nature of the data we will store:
1. We need to store billions of records
2. Each object we store is small (less than 1 kilobyte)
3. There are no relationships between records other than rstoring which user created a URL.
4. Our service is read-heavy.

## Database Schema
Need two tables: one for storing information about the URL mappings and one for the user's data who created the short link. 
### URL Table

$$
\begin{array}{|l|l|}
\hline \text { PK } & \text { Hash: varchar(16) } \\
\hline & \text { OriginalURL: varchar } \\
& \text { CreationDate: datetime } \\
& \text { ExpirationDate: datetime } \\
& \text { UserID: int } \\
\hline
\end{array}
$$

### User Table

$$
\begin{array}{|l|l|}
\hline \text { PK } & \text { UserID: Int } \\
\hline & \text { Name: varchar } \\
& \text { Email: datetime } \\
& \text { CreationDate: datetime } \\
& \text { LastLogin: datetime } \\
\hline
\end{array}
$$

## What kind of database should we use?
Since we anticipate storing billions of rows, and we don't need to use relationships between objects - a NoSQL store like DynamoDB, Cassandra, or Riak is a better choice. 

# Basic System Design and Algorithm
The problem we are solving is how to generate a short and unique key for a given URL.

## Encoding actual URL
We want to compute a unique hash of the given URL, so no matter the URL given, the resulting shortlink is always the same size. We then want to encode it for display.

A good question to ask ourselves is, what would a good length of a short key be? 6, 8, or 10 characters?

Using base64 encoding, a 6 letters long key would result in $64^6$ = ~68.7 billion possible strings.
Using base64 encoding, an 8 letters long key would result in $64^8$ = ~281 trillion possible strings.

With 68.7B unique strings, let's assume six letter keys would suffice for our system.

IF we use MD5 as the hash function, it will produce a 128-bit hash value. After base64 encoding, we'll get a string having more than 21 characters. Now we only have space for 6 characters per short key.. how will we choose our key? We can take the first 6 letters of the key, but that could result in duplication. To resolve that, we can choose some other characters out of the encoding string or swap some characters.

### Some different issues with our encoding scheme
1. If multiple users enter the same URL, they can get the same shortened URL, which is not acceptable.
2. What if parts of the URL are URL encoded? e.g.
```
http://www.test.com/distributed.php?id=design
http://www.test.com/distributed.php%3Fid%3Ddesign 
```
are identical except for the URL encoding.

#### Workaround for issues
We could append the user id (which should be unique) to the input URL. However, if the user is not signed in, we would have to ask the user to choose a uniqueness key.
