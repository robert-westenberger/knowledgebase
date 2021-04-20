---
title: Accessible Tables
description: 
published: true
date: 2021-04-20T02:33:59.382Z
tags: accessibility, html
editor: markdown
---

# TODO: Convert to html instead of markdown
# Layout vs Data Tables

## Data Tables
**Data tables** are the original intended use of table markup on the web. 

A table is a data table when row headers, column headers, or both are present that can be logically mapped to information within the table cells.

Below is a simple example of a data table. 
$$
\begin{aligned}
&\text { Shelly's Daughters }\\
&\begin{array}{|c|l|l|}
\hline \text { Name } & \text { Age } & \text { Birthday } \\
\hline \text { Jackie } & 5 & \text { April } 5 \\
\hline \text { Beth } & 8 & \text { January } 14 \\
\hline
\end{array}
\end{aligned}
$$

### Treatment By Screen Readers
It's important to use proper markup so a programmatic association can be made between table headers and cells. HTML provides two ways of accomplishing this:
* Headers and id attributes
* scope attributes



## Layout Tables
Don't have logical headers that can be mapped to information within the table cells.

### Treatment By Screen Readers
Screen readers will analyze table markup to determine if its a layout table. It is important that data table markup, such as \<th\>, \<caption\> etc are never used in layout tables, otherwise they will be identified as data tables.

Once identified as a layout table, screen readers read the content of layout tables based on the source code order. 