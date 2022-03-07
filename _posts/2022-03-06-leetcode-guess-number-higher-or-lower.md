---
title: "LeetCode: Guess Number Higher or Lower"
date: 2022-03-06T16:18:00-06:00
categories:
  - note
tags:
  - LeetCode
  - Python3
  - Easy
  - Binary Search
  - Interactive
toc_sticky: false
---

[Problem 374: Guess Number Higher or Lower]

[Problem 374: Guess Number Higher or Lower]: https://leetcode.com/problems/guess-number-higher-or-lower/

## Solution

### Thought process

- Fairly typical binary search problem.
- One tweak in this problem is that we know the number must exist, so there is really no need to have a terminal condition in the solution.

### Time complexity: $$O(\log N)$$

Simple binary search algorithm. $$N$$ refers to the total count of the integers from 1 to `n`.

### Space Complexity: $$O(1)$$

Only three integers are introduced: `l`, `r`, `mid`.

### Code

```py
class Solution:
    def guessNumber(self, n: int) -> int:
        l, r = 1, n
        while l <= r:
            mid = l + (r - l) // 2
            if guess(mid) == 0:
                return mid
            if guess(mid) == 1:
                l = mid + 1
            if guess(mid) == -1:
                r = mid - 1
        return mid
```

Since the number must exist, there is no need to set a termination condition if the number is not found.

```py
class Solution:
    def guessNumber(self, n: int) -> int:
        l, r = 1, n
        while True:
            mid = l + (r - l) // 2
            if guess(mid) == 0:
                return mid
            if guess(mid) == 1:
                l = mid + 1
            if guess(mid) == -1:
                r = mid - 1
```
