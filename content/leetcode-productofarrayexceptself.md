---
title: Solving the Product of Array Except Self Problem
description: Learn how to solve the Product of Array Except Self problem using Python. Understand the problem statement, explore different approaches, and implement the solution step by step. This is a medium difficulty question from LeetCode.
topic: Leetcode Daily
date: April 10, 2024
---

### Rating: Medium

#### [Link: LeetCode Product of Array Except Self Problem](https://leetcode.com/problems/product-of-array-except-self/description/)

The Product of Array Except Self problem is a coding interview question that involves finding the product of all elements in an array except for the current element. In this article, we will explore different approaches to solve this problem and implement the solution in Python.

## Problem Statement

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`. The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer. You must write an algorithm that runs in O(n) time and without using the division operation.

## Approach: Using Count of Zeros and Product of Non-Zero Numbers

This approach has a time complexity of O(n) because we traverse the list containing n elements only once.

The approach involves calculating the product of all non-zero numbers in the array and counting the number of zeros. If there is more than one zero in the array, the product of all numbers except for any given number will be zero. If there is exactly one zero, the product will be non-zero only for the zero element. If there are no zeros, the product for `nums[i]` is the total product divided by `nums[i]`.

```python
class Solution(object):
    def productExceptSelf(self, nums):
        total_product = 1
        zero_count = nums.count(0)

        if zero_count > 1:
            return [0] * len(nums)

        for num in nums:
            if num != 0:
                total_product *= num

        result = []
        for i in range(len(nums)):
            if zero_count == 0:
                result.append(total_product / nums[i])
            elif nums[i] == 0:
                result.append(total_product)
            else:
                result.append(0)

        return result
```
