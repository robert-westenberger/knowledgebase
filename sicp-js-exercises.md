---
title: sicp-js-exercises
description: SICP js exercises that don't have anywhere else to live right now
published: true
date: 2020-08-15T00:52:37.812Z
tags: 
editor: markdown
---

#### Exercise 2.21
(Note: This isn't as exactly as its found in SICP JS.. I rewrote it to use vanilla javascript methods / data structures )

The function square_list takes a list of numbers as argument and returns a list of the squares of those numbers.

console.log(square_list([1, 2, 3, 4]));
// [1, 4, 9, 16];

##### Answer
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
Implemenet for_each
for_each just applies the function to each of the elements in turn, from left to right. The values returned by applying the function to the elements are not used at all—for_each is used with functions that perform an action, such as printing. For example,

for_each(x => display(x), 
         list(57, 321, 88));
         
`57`
`321`
`88`

##### Answer

const for_each = (cb, elements) => {
    return (elements.length) ? [cb(elements.shift()), for_each(cb, elements)] : [];
};



