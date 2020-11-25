---
title: sicp-js-exercises
description: SICP js exercises that don't have anywhere else to live right now
published: true
date: 2020-11-25T21:22:47.218Z
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

#### Exercise 2.76 
* Generic operations with explicit dispatch - Each generic selector is implemented as a function that checks the tag of its argument and calls the appropriate function for handling data of that type. Whenever a new type is added, all existing generic functions need to be modified to include dispatch on new type.
```
function real_part(z) {
    return is_rectangular(z)
           ? real_part_rectangular(contents(z))
           : is_polar(z)
             ? real_part_polar(contents(z))
             : error(z, "Unknown type -- real_part");
}
function imag_part(z) {
    return is_rectangular(z)
           ? imag_part_rectangular(contents(z))
           : is_polar(z)
             ? imag_part_polar(contents(z))
             : error(z, "Unknown type -- imag_part");
}
function magnitude(z) {
    return is_rectangular(z)
           ? magnitude_rectangular(contents(z))
           : is_polar(z)
             ? magnitude_polar(contents(z))
             : error(z, "Unknown type -- magnitude");
}
function angle(z) {
    return is_rectangular(z)
           ? angle_rectangular(contents(z))
           : is_polar(z)
             ? angle_polar(contents(z))
             : error(z, "Unknown type -- angle");
}
```
* Data-directed style - Operation name and type ( for example, real_part and rectangular in a complex number system ) are used to lookup operation in a 2D table and call it. We don't need to know about how operations are represented internally. **This would be the best choice to add in new operations.**.. once  a new type is added one procedure for each operation must be written and installed in the 2D operations table. Once a new operation is added, it needs a representation for each type.
```
function install_rectangular_package() {
    // internal functions
    function real_part(z) { return head(z); }
    function imag_part(z) { return tail(z); }
    function make_from_real_imag(x, y) { return pair(x, y); }
    function magnitude(z) {
        return math_sqrt(square(real_part(z)) +
                         square(imag_part(z)));
    }
    function angle(z) {
        return math_atan(imag_part(z), real_part(z));
    }
    function make_from_mag_ang(r, a) {
        return pair(r * math_cos(a), r * math_sin(a));
    }

    // interface to the rest of the system
    function tag(x) {
        return attach_tag("rectangular", x);
    }
    put("real_part", list("rectangular"), real_part);
    put("imag_part", list("rectangular"), imag_part);
    put("magnitude", list("rectangular"), magnitude);
    put("angle", list("rectangular"), angle);
    put("make_from_real_imag", "rectangular",
        (x, y) => tag(make_from_real_imag(x, y)));
    put("make_from_mag_ang", "rectangular",
        (r, a) => tag(make_from_mag_ang(r, a)));
    return "done";
}
function install_polar_package() {
    // internal functions
    function magnitude(z) { return head(z); }
    function angle(z) { return tail(z); }
    function make_from_mag_ang(r, a) { return pair(r, a); }
    function real_part(z) {
       return magnitude(z) * math_cos(angle(z));
    }
    function imag_part(z) {
       return magnitude(z) * math_sin(angle(z));
    }
    function make_from_real_imag(x, y) {
       return pair(math_sqrt(square(x) + square(y)),
                   math_atan(y, x));
    }

    // interface to the rest of the system
    function tag(x) { return attach_tag("polar", x); }
    put("real_part", list("polar"), real_part);
    put("imag_part", list("polar"), imag_part);
    put("magnitude", list("polar"), magnitude);
    put("angle", list("polar"), angle);
    put("make_from_real_imag", "polar", 
        (x, y) => tag(make_from_real_imag(x, y)));
    put("make_from_mag_ang", "polar",
        (r, a) => tag(make_from_mag_ang(r, a)));
    return "done";
}
```
* Message-passing - Data objects receive messages that contain name of operation to be performed on the data. New data types need a new dispatch procedure that implements all of the operations. When a new operation is added each data type must alter its own dispatch procedure to dispatch on and perform the new operation.
```
function make_from_real_imag(x, y) {
    function dispatch(op) {
        return op === "real_part"
            ? x
            : op === "imag_part"
              ? y
              : op === "magnitude"
                ? math_sqrt(square(x) + square(y))
                : op === "angle"
                  ? math_atan(y, x)
                  : error(op,
                          "Unknown op -- make_from_real_imag");
    }
    return dispatch;
}
```
##### Exercise 2.77
When executing magnitude(z), the outermost tag is "complex" (since it is a complex number operation), so we have to add an operation to the operation table like so
```
put("magnitude", list("complex"), magnitude);
```
After the first call to magnitude strips off "complex", the second call to magnitude uses the "rectangular" tag to call the magnitude function inside the rectangular package.

#### Exercise 2.81
a. They are called in an infinite loop since apply_generic just keeps converting the types back and forth and calling apply_generic again (nothing changes).
b. apply_generic has to check if two args have the same type so as to not coerce them.