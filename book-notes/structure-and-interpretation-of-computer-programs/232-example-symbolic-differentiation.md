---
title: 2.3.2 Example: Symbolic Differentiation
description: 
published: true
date: 2020-08-24T01:36:11.530Z
tags: 
editor: markdown
---

# Example: Symbolic Differentiation



### Derivation function and representation of algebraic expressions

```
function is_same_variable(v1, v2) {
    return is_variable(v1) &&
        is_variable(v2) && v1 === v2;
}

function is_sum(x) {
    return is_pair(x) && head(x) === "+";
}

function make_sum(a1, a2) {
    return list("+", a1, a2);
}

function make_product(m1, m2) {
    return list("*", m1, m2);
}

function addend(s) {
    return head(tail(s));
}

function augend(s) {
    return head(tail(tail(s)));
}

function is_product(x) {
    return is_pair(x) && head(x) === "*";
}

function multiplier(s) {
    return head(tail(s));
}

function multiplicand(s) {
    return head(tail(tail(s)));
}

const error = (msg) => {
    console.error(msg);
}
function deriv(exp, variable) {
    return is_number(exp)
        ? 0
        : is_variable(exp)
            ? (is_same_variable(exp, variable)) ? 1 : 0
            : is_sum(exp)
                ? make_sum(deriv(addend(exp), variable),
                    deriv(augend(exp), variable))
                : is_product(exp)
                    ? make_sum(make_product(multiplier(exp),
                        deriv(multiplicand(exp),
                            variable)),
                        make_product(deriv(multiplier(exp),
                            variable),
                            multiplicand(exp)))
                    : error(exp,
                        "unknown expression type in deriv");
}
```
