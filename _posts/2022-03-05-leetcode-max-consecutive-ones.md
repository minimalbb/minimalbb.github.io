---
title: "LeetCode: Max Consecutive Ones"
date: 2022-03-05T16:46:00-06:00
categories:
  - note
tags:
  - LeetCode
  - Python3
  - Easy
  - Array
toc_sticky: false
---

[Problem 485: Max Consecutive Ones]

[Problem 485: Max Consecutive Ones]: https://leetcode.com/problems/max-consecutive-ones/

## Solution

### Thought process

- Need one integer `len_ans` tracking the **global** max length of consecutive ones
- Need another integer `len_temp` tracking the **local** length of consecutive ones
- Traverse through `nums`
  - Count length of consecutive ones by adding `len_temp` by 1
  - Reset the `len_temp` back to zero if the current number is not one, but make sure to compare against `len_ans` and update it if `len_temp` is larger.
- There is a possibility that `nums` does not end with 0. In that case, `len_ans` may only contain the length of the second to last group of consecutive ones. Check the values of `len_ans` and `len_ans` again. Update `len_ans` if `len_temp` is larger.

### Time complexity: $$O(N)$$

- One `for` loop walking through all of the elements in `nums`.

### Space Complexity: $$O(1)$$

- Defined only two additional variable `len_temp` and `len_ans` for storing integer.

### Code

```py
class Solution:
    def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
        len_temp = 0
        len_ans = 0
        for num in nums:
            if num == 1:
                len_temp += 1
            else:
                len_ans = len_temp if len_temp > len_ans else len_ans
                len_temp = 0
        len_ans = len_temp if len_temp > len_ans else len_ans
        return len_ans
```
