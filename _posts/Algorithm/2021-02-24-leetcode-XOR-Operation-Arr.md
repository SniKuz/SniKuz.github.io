---
title: "XOR Operation in an Array(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/maximum-gap/)
+ Given an integer n and an integer start.
+ Define an array nums where nums[i] = start + 2*i (0-indexed) and n == nums.length.
+ Return the bitwise XOR of all elements of nums.
**Example**

```
Input: n = 5, start = 0
Output: 8
Explanation: Array nums is equal to [0, 2, 4, 6, 8] where (0 ^ 2 ^ 4 ^ 6 ^ 8) = 8.
Where "^" corresponds to bitwise XOR operator.
```

```
//Python
class Solution(object):
    def xorOperation(self, n, start):
        """
        :type n: int
        :type start: int
        :rtype: int
        """
        temp = [start + i * 2 for i in range(0,n)]
        res = temp.pop(0)
        for i in temp:
            res = res ^ i
        return res
```
+ Runtime: 16 ms, faster than 76.78% of Python online submissions for XOR Operation in an Array.
+ Memory Usage: 13.3 MB, less than 73.45% of Python online submissions for XOR Operation in an Array.

---