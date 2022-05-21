---
title: Merge Two Sorted Linked Lists
description: 
published: true
date: 2022-05-21T21:12:56.921Z
tags: algorithms, linked-lists
editor: markdown
---

# Problem
You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists in a one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.



# Approach
## Iterative
### Implementation (Javascript)
```
const mergeTwoLists = function(l1, l2) {
    const head = new ListNode(-1);
    let ptr = head;
    while (l1 && l2) {
        if (l1.val > l2.val) {
            ptr.next = new ListNode(l2.val);
            l2 = l2.next;
        } else {
            ptr.next = new ListNode(l1.val);
            l1 = l1.next;
        }
        ptr = ptr.next;
    }
    ptr.next = l1 || l2;
    return head.next;
};
```
## Recursive
### Implementation (Javascript)
```
const mergeTwoLists = (l1, l2) => {
    if (l1 == null) {
        return l2;
    }
    if (l2 == null) {
        return l1;
    }
    if (l1.val < l2.val) {
        l1.next = mergeTwoLists(l1.next, l2);
        return l1;
    }
    l2.next = mergeTwoLists(l1, l2.next);
    return l2;
}
```