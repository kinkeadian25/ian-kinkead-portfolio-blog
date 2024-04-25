---
title: Solving the Invert Binary Tree Problem
description: Learn how to solve the LeetCode Invert Binary Tree problem using Python. Understand the problem statement, and see how I implemented the solution step by step in Python. This is a classic question from LeetCode and a great place to start with tree data structures.
topic: Leetcode
date: April 9, 2024
---

### Rating: Easy

#### [Link: LeetCode Invert Binary Tree Problem](https://leetcode.com/problems/invert-binary-tree/description/)

Learn how to solve the LeetCode Invert Binary Tree problem using Python. Understand the problem statement, and see how I implemented the solution step by step in Python. This is a classic question from LeetCode and a great place to start with tree data structures.

## Problem Statement

Given the root of a binary tree, invert the tree, and return its root.

Example 1:

Input: root = [4,2,7,1,3,6,9]
Output: [4,7,2,9,6,3,1]

Example 2:

Input: root = [2,1,3]
Output: [2,3,1]

Example 3:

Input: root = []
Output: []

Constraints:

The number of nodes in the tree is in the range [0, 100].
-100 <= Node.val <= 100

## Approach: Using Recursion

This approach has a time complexity of O(n) because we traverse the tree containing n nodes only once.

The simplest approach to solve the Invert Binary Tree problem is by using recursion. We can swap the left and right child of all nodes in the tree and return when a node is none or nil!

```python
class TreeNode(object):
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution(object):
    def invertTree(self, root):
        if root is None:
            return None

        (root.left, root.right) = (root.right, root.left)

        self.invertTree(root.left)
        self.invertTree(root.right)

        return root
```
