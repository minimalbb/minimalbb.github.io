---
title: "Binary Search Template"
date: 2022-03-06T14:24:00-06:00
categories:
  - cheat sheet
tags:
  - Python3
  - Binary Search
toc_sticky: false
---

This cheat sheet is based on [LeetCode Explore Binary Search].

[LeetCode Explore Binary Search]: https://leetcode.com/explore/learn/card/binary-search

It is better to use `l + (r - l) // 2` over `(l + r) // 2` because the latter could cause overflow while the former does not. Both approach will yield the same answer when there is no overflow issue.
{: .notice--danger}

The following table summarizes the distinguishing syntax elements between the three templates.

| Template | Initial Condition | Termination | Seaching Left | Searching Right |
| :------: | :---------------- | :---------- | :------------ | :-------------- |
| #1       | `l = 0, r = len-1`| `l > r`     | `r = mid - 1` | `l = mid + 1`   |
| #2       | `l = 0, r = len`  | `l == r`    | `r = mid`     | `l = mid + 1`   |

## Template 1

- Most basic one
- Search condition can be determined without comparing to the element's neighbors (or use specific elements around it).

| Template | Initial Condition | Termination | Seaching Left | Searching Right |
| :------: | :---------------- | :---------- | :------------ | :-------------- |
| #1       | `l = 0, r = len-1`| `l > r`     | `r = mid - 1` | `l = mid + 1`   |

```py
def binarySearch(nums, target):
    """
    :type nums: List[int]
    :type target: int
    :rtype: int
    """
    if len(nums) == 0:
        return -1

    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    # End Condition: left > right
    return -1
```

### Problmes Related to Template 1

- [Problem 69: Sqrt(x)]
- [Problem 374: Guess Number Higher or Lower]
- [Problem 33: Search in Rotated Sorted Array]

[Problem 69: Sqrt(x)]: https://leetcode.com/problems/sqrtx/
[Problem 374: Guess Number Higher or Lower]: https://leetcode.com/problems/guess-number-higher-or-lower/
[Problem 33: Search in Rotated Sorted Array]: https://leetcode.com/problems/search-in-rotated-sorted-array/

## Temoplate 2

- This template is used to search for an element or condition which requires accessing the current index and its immediate right neighbor's index in the array.
- Guarantees **Search Space is at least 2 in size at each step**
- Post-processing required. Loop/Recursion ends when you have 1 element left. Need to assess if the remaining element meets the condition.

| Template | Initial Condition | Termination | Seaching Left | Searching Right |
| :------: | :---------------- | :---------- | :------------ | :-------------- |
| #2       | `l = 0, r = len`  | `l == r`    | `r = mid`     | `l = mid + 1`   |

```py
def binarySearch(nums, target):
    """
    :type nums: List[int]
    :type target: int
    :rtype: int
    """
    if len(nums) == 0:
        return -1

    left, right = 0, len(nums)
    while left < right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid

    # Post-processing:
    # End Condition: left == right
    if left != len(nums) and nums[left] == target:
        return left
    return -1
```

### Problmes Related to Template 2

- [Problem 278: First Bad Version]
- [Problem 162: Find Peak Element]
- [Problem 153: Find Minimum in Rotated Sorted Array]

[Problem 278: First Bad Version]: https://leetcode.com/problems/first-bad-version/
[Problem 162: Find Peak Element]: https://leetcode.com/problems/find-peak-element/
[Problem 153: Find Minimum in Rotated Sorted Array]: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/

## Temoplate 3

TBD

### Problmes Related to Template 3

TBD