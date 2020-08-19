---
title: sicp-js-exercises
description: SICP js exercises that don't have anywhere else to live right now
published: true
date: 2020-08-19T01:03:24.365Z
tags: 
editor: markdown
---

#### Exercise 2.21
(Note: This isn't as exactly as its found in SICP JS.. I rewrote it to use vanilla javascript methods / data structures )

The function square_list takes a list of numbers as argument and returns a list of the squares of those numbers.


##### Answer
```
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
```
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
```
const for_each = (cb, elements) => {
    return (elements.length) ? [cb(elements.shift()), for_each(cb, elements)] : [];
};
```
#### Exercise 2.37
See [matrix](/mathematics/matrix) (basic matrix operations)

#### Exercise 2.41
> Write a function to find all ordered triples of distinct positive integers i, j, and k less than or equal to a given integer n that sum to a given integer s.

##### Answer
```
const unique_triples = (n) => {
    return flatmap(i => flatmap(j => map(k => list(i, j, k),
        enumerate_interval(1, j - 1)),
        enumerate_interval(1, i - 1)),
        enumerate_interval(1, n));
}
const does_sum_to_s = (item, s) => {
    const first_integer = head(item);
    const second_integer = head(tail(item));
    const third_integer = head(tail(tail(item)));
    return plus(first_integer, plus(second_integer, third_integer)) === s;
}
const uniqueSumTriples = (n, s) => {
    const triples = unique_triples(n);
    return filter((item) => {
        return does_sum_to_s(item, s);
    }, triples);
}
```