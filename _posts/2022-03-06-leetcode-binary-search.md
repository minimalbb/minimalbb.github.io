---
title: "LeetCode: Binary Search"
date: 2022-03-06T14:24:00-06:00
categories:
  - note
tags:
  - LeetCode
  - Python3
  - Easy
  - Array
  - Binary Search
toc_sticky: false
---

[Problem 704: Binary Search]

[Problem 704: Binary Search]: https://leetcode.com/problems/binary-search/

## Solution

### Thought process

- In the end, there must be a `return -1` when `target` is not found.
- Starting off with the left pointer pointing at the first element and right pointer pointing at the last element.
- Take the element in the middle to see if it is target.
  - If it is equal to `target`, then `return` the index
  - If it is not equal to `target`, check whether the middle element is larger than or less than `target`
    - If the middle element is larger than `target`, then `target` could be on the left. Move the right pointer to the left of middle pointer.
    - If the middle element is less than `target`, then `target` could be on the right. Move the left pointer to the right of middle pointer.

### Time complexity: $$O(\log N)$$

- Binary search slice the list in half in each iteration, so the time compleity for it to determine whether a number is found or not found is going to be $$O(\log N)$$.

### Space Complexity: $$O(1)$$

- Only three integers: `l`, `r` and `mid` are introduced.

### Code

```py
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1
        while l <= r:
            mid = (l + r) // 2
            if nums[mid] == target:
                return mid
            if nums[mid] > target:
                r = mid - 1
            else:
                l = mid + 1
        return -1
```
