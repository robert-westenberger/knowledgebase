---
title: sicp-js-exercises
description: SICP js exercises that don't have anywhere else to live right now
published: true
date: 2020-11-16T18:51:37.384Z
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
#### Exercise 2.42 / 2.43
Skipped for now

#### Exercise 2.53
list("a", "b", "c");
`["a", ["b", ["c"]]];`
list(list("george"));
`[["george", null]];`
tail(list(list("x1", "x2"), list("y1", "y2")));
`[["y1", ["y2", null]], null]`
tail(head(list(list("x1", "x2"), list("y1", "y2"))));
`["x2", null]`


#### Exercise 2.54
Two lists are said to be equal if they contain equal elements arranged in the same order. For example,

```equal(list("this", "is", "a", "list"), 
      list("this", "is", "a", "list"));
```      
is true but 

```equal(list("this", "is", "a", "list"),
      list("this", list("is", "a"), "list"));
```
      
is false. To be more precise, we can define equal recursively in terms of the basic === equality of strings by saying that a and b are equal with respect to equal if they are both strings and the strings are equal with respect to ===, or if they are both lists such that head(a) is equal with respect to equal to head(b) and tail(a) is equal with respect to equal to tail(b). Using this idea, implement equal as a function.

```const equal = (a, b) => {
    if (is_pair(a) && is_pair(b)) {
        return equal(tail(a), tail(b)) && equal(head(a), head(b));
    }
    return a === b;
}
```

Book answer is way more robust, testing multiple types..
```
function equal(xs, ys) {
    return is_pair(xs)
        ? (is_pair(ys) &&
           equal(head(xs), head(ys)) && 
           equal(tail(xs), tail(ys)))
        : is_null(xs)
        ? is_null(ys)
        : is_number(xs)
        ? (is_number(ys) && xs === ys)
        : is_boolean(xs)
        ? (is_boolean(ys) && ((xs && ys) || (!xs && !ys)))
        : is_string(xs)
        ? (is_string(xs) && xs === ys)
        : is_undefined(xs)
        ? is_undefined(ys)
        : // we know now that xs is a function
          (is_function(ys) && xs === ys);
}
```

#### Exercise 2.57

```
function multiplier(s) {
    return head(tail(s));
}

function multiplicand(s) {
    return accumulate(make_product, 1, tail(tail(s)));
}
```
#### Exercise 2.58 
Skipped for now

#### Exercise 2.73
a. The deriv function was refactored to use data-directed programming. The operator of the expression is the "type" key passed to *get*. Is_number and is_variable cannot be assimilated because there is no type key associated with them.
d. If the functions were indexed the opposite way, the keys used to install the derivative system need to be switched. So we need to go from 
to
```
put("deriv", "*", mult);
put("deriv", "+", add);
```
```
put("*", "deriv", mult);
put("+", "deriv", add);
```
