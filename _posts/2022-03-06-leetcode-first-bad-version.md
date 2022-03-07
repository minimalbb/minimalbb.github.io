---
title: "LeetCode: First Bad Version"
date: 2022-03-06T23:16:00-06:00
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

[Problem 278: First Bad Version]

[Problem 278: First Bad Version]: https://leetcode.com/problems/first-bad-version/

## Solution

### Thought process

The key of this problem is that we have to find the **first** bad version which means we not only have to look at `i` version, but also `i-1` version in each search. In order to make sure the `i` version is the first bad version, two conditions must be met:

1. `i` version has to be bad
2. `i-1` version has to be good

Since we not only have to look for one element to satisfy the condition but also have to look at the one immediately before it, it is best to use the binary search algorithm with at least two elements in every search window. 

Note that there is a chance where only the last version is bad. Therefore, we need to consider that particular case after the binary search terminates.
{: .notice--primary}

### Time complexity: $$O(\log N)$$

Cost of binary search is $$O(\log N)$$.

### Space Complexity: $$O(1)$$

Only three integers are introduced: `l`, `r`, `i`.

### Code

```py
class Solution:
    def firstBadVersion(self, n: int) -> int:        
        l, r = 1, n
        while l <= r:
            i = l + (r - l) // 2
            isBad_i = isBadVersion(i)
            isBad_im1 = isBadVersion(i - 1)
            if isBad_i and not isBad_im1:
                return i
            if not isBad_i:
                l = i + 1
            else:
                r = i
        if l != n and isBadVersion(l):
            return l
```
