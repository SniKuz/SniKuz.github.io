---
title: "Maximum Gap(Hard)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/maximum-gap/)
+ Given an unsorted array, find the maximum difference between the successive elements in its sorted form.
+ Return 0 if the array contains less than 2 elements.
**Example**

```
Input: [3,6,9,1]
Output: 3
Explanation: The sorted form of the array is [1,3,6,9], either
             (3,6) or (6,9) has the maximum difference 3.
```

```
//Python
class Solution(object):
    def flipAndInvertImage(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        result = []
        for i in range(0, len(A)):
                A[i].reverse()
        for i in range(0, len(A)):
            for j in range(0, len(A[i])):
                if A[i][j] == 0: A[i][j] = 1
                else: A[i][j] = 0
        return A
```
+ Runtime: 40 ms, faster than 71.43% of Python online submissions for Maximum Gap.
+ Memory Usage: 14.2 MB, less than 42.11% of Python online submissions for Maximum Gap.
---