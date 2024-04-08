---
title: Solving the Two Sum Problem
description: Learn how to solve the Two Sum problem using Python. Understand the problem statement, explore different approaches, and implement the solution step by step. This is probably the easiest question from the Blind 75 and a great place to start with DSA.
topic: Leetcode Daily
date: April 7, 2024
---

### Rating: Easy

#### [Link: LeetCode Two Sum Problem](https://leetcode.com/problems/two-sum/description/)

The Two Sum problem is a classic coding interview question that involves finding two numbers in an array that add up to a given target value and returning their indices. In this article, we will explore different approaches to solve this problem and implement the solution in Python.

## Problem Statement

Given an array of integers `nums` and a target value `target`, find two numbers in the array such that they add up to `target`. You may assume that each input would have exactly one solution, and you may not use the same element twice.

## Approach 1: Brute Force

This approach has a time complexity of O(n^2) because in the worst case, we would need to compare each element with every other element in the array.

The simplest approach to solve the Two Sum problem is by using a brute force method. We can iterate through each element in the array and check if there is another element that, when added to the current element, equals the target value.

```python
def twoSum(nums, target):
    for i in range(len(nums)):
        for j in range(i+1, len(nums)):
            if nums[j] == target - nums[i]:
                return [i, j]
    return []
```

## Approach 2: Optimal - Using a dictionary

This approach has a time complexity of O(n) because we traverse the list containing n elements only once. Each lookup in the table costs only O(1) time.

The optimal approach involves using a dictionary to reduce the time complexity. We can maintain a dictionary where the keys are the numbers in the array and the values are their indices.

While we iterate over the array, we check if target - nums[i] is present in the dictionary. If it is, we have found a pair of elements that sum up to the target. If it's not, we insert nums[i] into the dictionary and continue to the next iteration.

```python
def twoSum(nums, target):
    num_map = {}
    for i, num in enumerate(nums):
        diff = target - num
        if diff in num_map:
            return [num_map[diff], i]
        num_map[num] = i
    return []
```
