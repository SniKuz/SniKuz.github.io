---
title: "Kth Missing Positive Number(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/kth-missing-positive-number/)
+ Given an array arr of positive integers sorted in a strictly increasing order, and an integer k.
+ Find the kth positive integer that is missing from this array.
**Example**

```
Input: arr = [2,3,4,7,11], k = 5
Output: 9
Explanation: The missing positive integers are [1,5,6,8,9,10,12,13,...]. The 5th missing positive integer is 9.
```

```
//Python
class Solution(object):
    def findKthPositive(self, arr, k):
        """
        :type arr: List[int]
        :type k: int
        :rtype: int
        """
        result = [i for i in range(0, 100000)]
        for i in arr:
            result.remove(i)
        return result[k]
```
+ Runtime: 748 ms, faster than 5.05% of Python online submissions for Kth Missing Positive Number.
+ Memory Usage: 17.5 MB, less than 5.37% of Python online submissions for Kth Missing Positive Number.
---
꼼수로 풀은듯한...