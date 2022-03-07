---
title: "LeetCode: Search in Rotated Sorted Array"
date: 2022-03-06T18:04:00-06:00
categories:
  - note
tags:
  - LeetCode
  - Python3
  - Medium
  - Array
  - Binary Search
toc_sticky: false
---

[Problem 33: Search in Rotated Sorted Array]

[Problem 33: Search in Rotated Sorted Array]: https://leetcode.com/problems/search-in-rotated-sorted-array/

## Solution

### Thought process

- Since the question asks us to write an algorithm with $$O(\log N)$$ runtime complexity, **intuition tells us to use binary search algorithm**.
- For binary search algorithm to work, the array has to be sorted which is not the case for this problem. (At least from the plain sight.)
- Since the array `nums` is **possibly rotated** after sorting in ascending order, there will be three scenarios as shown in the figure below.
  1. The first scenario is the trivial case where the array happens to be sorted
  2. The second scenario has the rotation relatively further where the minimum value is closer to the end of the array.
  3. The third scenatio has the rotation relatively closer where the minimum value is closer to the start of the array.

:bulb: If we can know where the minimum value is, then we could target the specific sub-array with binary search to find the existence of `target` value and its corresponding index.
{: .notice}

**Question is how to find the index of the minimum value?**

:bulb: The 1st key is to recognize the characteristic of the minimum value.
{: .notice}

Because the array is **strictly acending** before rotating, `nums[i-1] > nums[i]` is true if and only if `i` is located at the minimum value.

:bulb: The 2nd key is to devise a searching strategy that helps us know which part to search for based on the scenarios on the table.
{: .notice}

If we take a closer look at the three scenarios, there is actually a way to find the index of minimum value also by binary search algorithm. Assume the following 

- `l` pointer is pointing to the left most element
- `r` pointer is pointng to the right most element
- `i` is in the middle of `l` and `r`

1. In the 1st scenario, it is known that `nums[l] < nums[r]` and `nums[l] < nums[i]`. Thus, the binary search should **search the left half** by `r = i - 1`.
2. In the 2nd scenario, it is known that `nums[l] > nums[r]` and `nums[l] < nums[i]`. Thus, the binary search should **search right half** by `l = i + 1`
3. In the 3rd scenario, it is known that `nums[l] > nums[r]` and `nums[l] > nums[i]`. Thus,the binary search should **search the left half** by `r = i - 1`.

Based on the above three points, we can use binary search algorithm to determine the index of the minimum value in the rotated sorted array. To summarize, we divide the problem into two parts

  1. Use binary search algorithm to find the index of the minimum value in the array.
  2. Use binary search algorithm to find the index of `target` within the sub-array.

![Three possible scenarios](/assets/images/2022-03-06-leetcode-search-in-sorted-array-scenario.png "Three possible scenarios")

### Time complexity: $$O(\log N)$$

We use the binary search algorithm for two times. Therefore, it is constant times of $$O(\log N)$$.

### Space Complexity: $$O(1)$$

Only three integers are introduced: `l`, `r`, `i`.

### Code

```py
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1
        while l <= r:
            i = l + (r - l) // 2
            if nums[i] < nums[i - 1]:
                break
            if nums[i] >= nums[l] and nums[l] > nums[r]:
                l = i + 1
            else:
                r = i - 1
        
        if nums[i] <= target and target <= nums[len(nums) - 1]:
            l, r = i, len(nums) - 1
        else:
            l, r = 0, i - 1
        
        while l <= r:
            i = l + (r - l) // 2
            if nums[i] == target:
                return i
            if nums[i] < target:
                l = i + 1
            else:
                r = i - 1
        return -1
```
