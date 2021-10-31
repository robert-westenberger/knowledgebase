---
title: Detect Loop In Linked List
description: 
published: true
date: 2021-10-31T03:22:42.677Z
tags: algorithms
editor: markdown
---

# Hashing Approach

Traverse the list one by one and keep putting the node addresses in a Hash Table. At any point, if NULL is reached then return false, and if the next of the current nodes points to any of the previously stored nodes in  Hash then return true.

# Floyd's Cycle-Finding Algorithm
Traverse the linked list using two pointers. Move one pointer by one and another by two. If the pointers meet at the same node then there is a loop. If pointers do not meet then the linked list doesn't have a loop. 

## C Implementation
```
struct ListNode
{
  int val;
  struct ListNode *next;
};

bool hasCycle(struct ListNode *head)
{
  struct ListNode* fast = head;
  struct ListNode* slow = head;
  while (slow && fast && fast->next) {
    slow = slow->next;
    fast = fast->next->next;
    if (slow == fast) {
      return true;
    }
  }
  return false;
}
```