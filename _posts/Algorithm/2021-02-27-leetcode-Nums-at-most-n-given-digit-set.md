---
title: "Numbers At Most N Given Digit Set(Hard)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/numbers-at-most-n-given-digit-set/)
+ Given an array of digits which is sorted in non-decreasing order. You can write numbers using each digits[i] as many times as we want. For example, if digits = ['1','3','5'], we may write numbers such as '13', '551', and '1351315'.
+ Return the number of positive integers that can be generated that are less than or equal to a given integer n.
**Example**

```
Input: digits = ["1","3","5","7"], n = 100
Output: 20
Explanation: 
The 20 numbers that can be written are:
1, 3, 5, 7, 11, 13, 15, 17, 31, 33, 35, 37, 51, 53, 55, 57, 71, 73, 75, 77.
```

```
class Solution(object):
    def atMostNGivenDigitSet(self, digits, n):
        """
        :type digits: List[str]
        :type n: int
        :rtype: int
        """
        global cnt
        cnt = 0
        def recursiveCheck(m):
            if int(m) > n: return 0
            global cnt
            cnt += 1
            for i in digits:
                temp = m + i
                recursiveCheck(temp)

        for i in digits:
            recursiveCheck(i)
        return cnt

#다른분의 Solution
    class Solution(object):
        def atMostNGivenDigitSet(self, digits, n):
            """
            :type digits: List[str]
            :type n: int
            :rtype: int
            """
            digits = set(map(int, digits))
            sn = str(n)
            ln = len(sn)
            cnt = 0

            for l in range(1, ln):
                cnt += len(digits) ** l
            for i, dn in enumerate(sn):
                dn = int(dn)
                less_than = sum(d < dn for d in digits)
                print(less_than)
                cnt += less_than * len(digits) ** (ln - i - 1)
                if dn not in digits:
                    break
                elif i == ln - 1:
                    cnt += 1
            return cnt
```
+ Runtime: 60 ms, faster than 92.31% of Python online submissions for Rotate Function.
+ Memory Usage: 14.9 MB, less than 51.28% of Python online submissions for Rotate Function.
---
단순히 재귀함수로 작성해 봤는데 문제를 분석하면 점화식 f(i+1) = f(i) + sum(Arr) - last element * len(Arr)이 나오고 이를 토대로 함수를 재작성 하는 방식에 대한 고민이 필요. 기존 독서에서 다음 부분을 더 자세히 이해해야할 것 같음