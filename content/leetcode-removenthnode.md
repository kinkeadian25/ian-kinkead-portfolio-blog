---
title: Solving the Remove Nth Node From End of List Problem
description: Learn how to solve the Remove Nth Node From End of List problem using Python. Understand the problem statement, grasp the theory, and implement the solution. This is good practice for linked list problems.
topic: Leetcode Daily
date: April 7, 2024
---

### Rating: Medium

#### [Link: LeetCode Remove Nth Node From End of List Problem](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)

The Remove Nth Node From End of List problem is a common coding interview question that involves manipulating a linked list. In this article, we will explore different approaches to solve this problem and implement the solution in Python.

## Problem Statement

Given the head of a linked list, remove the nth node from the end of the list and return its head.

## Approach: Two Pointers

This approach has a time complexity of O(L), where L is the length of the list, because we traverse the list containing L elements only once.

The optimal approach involves using two pointers to traverse the list. We can maintain a "fast" pointer and a "slow" pointer. The "fast" pointer moves n steps ahead first. If it reaches the end, we remove the head of the list. Otherwise, we move both pointers until the "fast" pointer reaches the end. The "slow" pointer will then be pointing at the previous node of the target node.

```python
def removeNthFromEnd(self, head, n):
    dummy = ListNode(0)
    dummy.next = head
    fast = head
    slow = head

    for i in range(n):
        fast = fast.next

    if not fast:
        return head.next

    while fast.next:
        slow = slow.next
        fast = fast.next

    slow.next = slow.next.next
    return dummy.next
```
