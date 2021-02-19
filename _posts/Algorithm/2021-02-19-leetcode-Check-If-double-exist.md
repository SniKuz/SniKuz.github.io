---
title: "Check if double exist(easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/check-if-n-and-its-double-exist/)
+ Given an array arr of integers, check if there exists two integers N and M such that N is the double of M ( i.e. N = 2 * M).
+ More formally check if there exists two indices i and j such that : @
---
**Example**

```
Input: arr = [10,2,5,3]
Output: true
Explanation: N = 10 is the double of M = 5,that is, 10 = 2 * 5.
```

```
//Python
class Solution(object):
    def checkIfExist(self, arr):
        """
        :type arr: List[int]
        :rtype: bool
        """
        for i in arr:
            if i == 0:
                if arr.count(i) >1:
                    return True
            elif arr.count(i*2) > 0:
                return True
        return False
```
+ Runtime: 32 ms, faster than 95.34% of Python online submissions for Check If N and Its Double Exist.
+ Memory Usage: 13.6 MB, less than 37.71% of Python online submissions for Check If N and Its Double Exist.
