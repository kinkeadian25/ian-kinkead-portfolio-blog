---
title: Solving the Best Time to Buy and Sell Stock Problem
description: Learn how to solve the Best Time to Buy and Sell Stock problem using Python. Understand the problem statement, grasp the theory, and implement the solution. This is good practice for array problems.
topic: Leetcode Daily
date: April 8, 2024
---

### Rating: Easy

#### [Link: LeetCode Best Time to Buy and Sell Stock Problem](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

The Best Time to Buy and Sell Stock problem is a common coding interview question that involves manipulating an array. In this article, we will explore different approaches to solve this problem and implement the solution in Python.

## Problem Statement

You are given an array prices where prices[i] is the price of a given stock on the ith day. You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock. Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

## Approach: One Pass - Sliding Window

This approach has a time complexity of O(n), where n is the length of the array, because we traverse the array containing n elements only once.

The optimal approach involves using two pointers to traverse the array. We can maintain a "left" pointer and a "right" pointer. The "right" pointer moves one step ahead each time. If the new profit is negative, we move the "left" pointer to the "right" pointer's position. Otherwise, we update the profit to the maximum profit.

```python
class Solution(object):
    def maxProfit(self, prices):
        L = 0
        R = 1

        profit = 0
        while R < len(prices):
            new_profit = prices[R] - prices[L]

            if new_profit < 0:
                L = R
                R += 1
            else:
                profit = max(profit, new_profit)
                R += 1
        return profit
```
