---
title: "LeetCode: Squares of a Sorted Array"
date: 2022-03-06T14:06:00-06:00
categories:
  - note
tags:
  - LeetCode
  - Python3
  - Easy
  - Array
  - Two Pointers
  - Sorting
toc_sticky: false
---

[Problem 977: Squares of a Sorted Array]

[Problem 977: Squares of a Sorted Array]: https://leetcode.com/problems/squares-of-a-sorted-array/

## Solution

### Thought process

The brute force solution is to calculate the squares and then sort. However, this approach is too trivial and would lead to $$O(N \log N)$$ runrime complexity.

To achieve $$O(N)$$ runtime complexity, we simply cannot have sorting algorithm involved in the process. An efficient way to get the squares of a sorted array can be achieved by using binary searching and two-pointers approach combined:

1. Find the element having the smallest absolute value at index `i` using binary search
2. Maintain two pointers `l` and `r` on both sides of `i`
   1. Determine which absolute value is smaller between `nums[l]` and `nums[r]`
   2. Go one step further (left `l = l - 1` or right `r = r + 1`) if it is determined to have smaller absolute value
   3. Repeat until one pointer reach the start or the end of array
3. Complete computing sqaures on the un-finished sides

### Time complexity: $$O(N)$$

The cost of binary search is $$O(\log N)$$ and the cost of traversing array with two-pointer is $$O(N)$$. Since the most expensive process dominates, the overall time complexity is $$O(N)$$.

### Space Complexity: $$O(1)$$

Only introduced 4 integers: `l`, `r`, `i`, `minval`. So space complexity is $$O(1)$$ if not considering the returning array `ans`.

### Code

```py
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        l = 0
        r = len(nums) - 1
        if nums[l] < 0 and nums[r] < 0:
            i = r
            minval = nums[i] ** 2
        elif nums[l] >= 0 and nums[r] >= 0:
            i = l
            minval = nums[i] ** 2
        else:
            minval = nums[l] ** 2
            while l < r or minval == 0:
                i = l + (r - l) // 2
                if nums[i] ** 2 < minval:
                    minval = nums[i] ** 2
                if nums[i-1] ** 2 < nums[i] ** 2:
                    r = i - 1
                else:
                    l = i + 1
        
        ans = []
        ans.append(minval)
        
        l, r = i - 1, i + 1
        while l >= 0 and r <= len(nums) - 1:
            if nums[l] ** 2 < nums[r] ** 2:
                ans.append(nums[l] ** 2)
                l = l - 1
            else:
                ans.append(nums[r] ** 2)
                r = r + 1
        while l >= 0:
            ans.append(nums[l] ** 2)
            l = l - 1
        while r <= len(nums) - 1:
            ans.append(nums[r] ** 2)
            r = r + 1
        return ans
```
