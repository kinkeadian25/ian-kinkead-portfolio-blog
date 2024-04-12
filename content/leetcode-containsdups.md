---
title: Solving the Contains Duplicate Problem
description: Learn how to solve the Contains Duplicate problem using Python. Understand the problem statement, explore different approaches, and implement the solution step by step. This is an easy difficulty question from LeetCode.
topic: Leetcode Daily
date: April 11, 2024
---

### Rating: Easy

#### [Link: LeetCode Contains Duplicate Problem](https://leetcode.com/problems/contains-duplicate/description/)

The Contains Duplicate problem is a coding interview question that involves checking if an array contains any duplicate elements. In this article, we will explore different approaches to solve this problem and implement the solution in Python.

## Problem Statement

Given an integer array `nums`, return true if any value appears at least twice in the array, and return false if every element is distinct.

## Approach: Using a Dictionary

This approach has a time complexity of O(n) because we traverse the list containing n elements only once.

The approach involves using a dictionary to keep track of the elements we have seen so far. If we encounter an element that is already in the dictionary, we return true because it is a duplicate. If we traverse the entire array without finding any duplicates, we return false.

```python
class Solution(object):
    def containsDuplicate(self, nums):
        seen_nums = {}

        for i in range(len(nums)):
            if nums[i] in seen_nums:
                return True
            else:
                seen_nums[nums[i]] = nums[i]
        return False
```
