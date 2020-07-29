---
title: sicp-js-exercises
description: SICP js exercises that don't have anywhere else to live right now
published: true
date: 2020-07-29T02:05:18.052Z
tags: 
editor: markdown
---

#### Exercise 2.21
(Note: This isn't as exactly as its found in SICP JS.. I rewrote it to use vanilla javascript methods / data structures )

The function square_list takes a list of numbers as argument and returns a list of the squares of those numbers.

console.log(square_list([1, 2, 3, 4]));
// [1, 4, 9, 16];

const squareList1 = (items) => {
    return items.map((item) => {
        return item * item;
    });
}

const squareList2 = (items) => {
    const current_val = items.shift();
    return items.length === 0 ?
        [current_val * current_val] :
        [current_val * current_val, ...squareList2(items)];
}

#### Exercise 2.22
Q/A question - skipped for now
#### Exercise 2.23
