---
title: "LeetCode: Sqrt(x)"
date: 2022-03-06T14:49:00-06:00
categories:
  - note
tags:
  - LeetCode
  - Python3
  - Easy
  - Math
  - Binary Search
toc_sticky: false
---

[Problem 69: Sqrt(x)]

[Problem 69: Sqrt(x)]: https://leetcode.com/problems/sqrtx/

## Solution

### Thought process

- Since the problem prohibits any use of power function or operator, we must use search algorithm to find the value of `sqrt(x)`.
- The search space would be all integers from 0 to `x`.
- Strategy is to use the typical binary search. To begin with, the left pointer `l` points to 0 and the right pointer `r` points to `x`.
- If the exact square root value is found, the search algorithm terminates.
- If the exact square root value is not found, the right pointer `r` will always appear on the immediate left hand side of the left pointer `l` in the end due to the termination condition. Namely, `r == l - 1` is true.
- Whether `l` was moved to the right or  `r` was moved to the left in the last step does not matter, it will always become `nums[r] < sqrt(x) < nums[l]` when there is no perfect square found. Based on the request of the question, we need to return `r` in the end.

### Time complexity: $$O(\log N)$$

Simple binary search algorithm. $$N$$ refers to the total count of the integers from 0 to `x`.

### Space Complexity: $$O(1)$$

Only three integers are introduced: `l`, `r`, `mid`.

### Code

```py
class Solution:
    def mySqrt(self, x: int) -> int:
        l, r = 0, x
        while l <= r:
            mid = (l + r) // 2
            if mid * mid == x:
                return mid
            if mid * mid < x:
                l = mid + 1
            else:
                r = mid - 1
        return r
```
