---
title: "LeetCode: Find Numbers with Even Number of Digits"
date: 2022-03-05T16:50:00-06:00
categories:
  - note
tags:
  - LeetCode
  - Python3
  - Easy
  - Array
toc_sticky: false
---

[Problem 1295: Find Numbers with Even Number of Digits]

[Problem 1295: Find Numbers with Even Number of Digits]: https://leetcode.com/problems/find-numbers-with-even-number-of-digits/

## Solution 1

### Thought process 1

One approach is to use number of division to determine number of digits.

- Divide number by 10 until it is less than 10. Count the number of division along the way.
- If the number of division happens to be an odd number, the number has even number of digits.
- Use a counter to count the total number of elements with even digits.

Use the list `[12,345,2,6,7896]` as example:

- 12 / 10 = 1.2 -> 1.2 < 10
- 345 / 10 = 34.5 -> 34.5 / 10 = 3.45 -> 3.45 < 10
- 2 < 10
- 6 < 10
- 7896 / 10 = 789.6 -> 789.6 / 10 = 78.96 -> 78.96/10 = 7.896 -> 7.896 < 10

### Time complexity 1: $$O(N)$$

One `for` loop iterate through the elementss of `nums`. Each element is divided by 10 until it is less than zero. Since number is between 1 to 10000, so a number will be divided four times (constant time) in worst case.

### Space Complexity 1: $$O(1)$$

Three integers: `temp`, `num_div` and `counter`. So, only a constant order.

### Code 1

```py
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        counter = 0
        for num in nums:
            num_div = 0
            temp = num
            while temp >= 10:
                temp = temp / 10
                num_div += 1
            if num_div % 2 == 1:
                counter += 1
        return counter
```

## Solution 2

### Thought process 2

The other approach is to convert each element into a string. Then, use the length of string to determine the number of digits.

- Convert number into string.
- Count length of the string.
- If the length of the string happens to be an even number, the element will also have even digits.
- Use a counter to count the total number of elements with even digits.

Use the list `[12,345,2,6,7896]` as example:

- 12 -> `'12'` -> `len('12')` is 2
- 345 -> `'345'` -> `len('345')` is 3
- 6 -> `'6'` -> `len('6')` is 1
- 7896 -> `'7896'` -> `len('7896')` is 4

### Time complexity 2: $$O(N)$$

One `for` loop iterate through the elementss of `nums`.

### Space Complexity 2: $$O(1)$$

One integer `counter`, Temporarily, there will be one string with at most five characters and another integer.

### Code 2

```py
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        counter = 0
        for num in nums:
            if len(str(num)) % 2 == 0:
                counter += 1
        return counter
```
