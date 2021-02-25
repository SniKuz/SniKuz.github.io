---
title: "N-th Tribonacci Number(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/n-th-tribonacci-number/)
+ The Tribonacci sequence Tn is defined as follows: 
+ T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.
+ Given n, return the value of Tn.
**Example**

```
Input: n = 4
Output: 4
Explanation:
T_3 = 0 + 1 + 1 = 2
T_4 = 1 + 1 + 2 = 4
```

```
//Python
class Solution(object):
    def tribonacci(self, n):
        """
        :type n: int
        :rtype: int
        """
        Tn = [0, 1, 1]
        for i in range(3, n+1):
            Tn.append(Tn[i-3] + Tn[i-2] + Tn[i-1])
        return Tn[n]
```
+ Runtime: 20 ms, faster than 42.86% of Python online submissions for N-th Tribonacci Number.
+ Memory Usage: 13.4 MB, less than 40.82% of Python online submissions for N-th Tribonacci Number.



---