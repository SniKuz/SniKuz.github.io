---
title: " Numbers With Repeated Digits(Hard)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/numbers-with-repeated-digits/)
+ Given a positive integer N, return the number of positive integers less than or equal to N that have at least 1 repeated digit.
**Example**

```
Input: 101
Output: 11
Explanation: The positive numbers (<= 100) with atleast 1 repeated digit are 11, 22, 33, 44, 55, 66, 77, 88, 99,100 and 101
```

```
//Python
//초기 시도
class Solution(object):
    def numDupDigitsAtMostN(self, N):
        """
        :type N: int
        :rtype: int
        """
        result = 0
        for i in range(10, N+1):
            temp = str(i)
            temp = list(temp)
            for j in range(0, 10):
                if temp.count(str(j)) > 1:
                    result += 1
                    break
        return result
//1차 변형
from collections import Counter

class Solution(object):
    def numDupDigitsAtMostN(self, N):
        result = 0
        digit = [0,1,2,3,4,5,6,7,8,9]
        temp = [i for i in range(10, N+1)]
        for i in temp:
            i = str(i)
            counter = Counter(i)
            for letter in counter:
                if counter[letter] > 1:
                    result += 1
                    break
        return result

//2차 변형
class Solution(object):
    def numDupDigitsAtMostN(self, N):
        result = 0
        for i in range(10, N+1):
            i = str(i)
            if Counter(i).most_common(1)[0][1] > 1:
                result += 1
        return result
```
---
세 코드 모두 문제는 없는 것 같은데 Time Limit Exceed가 걸린다.
다른 분들을 참고해보니 파이썬을 사용한 경우 leetcode의 Judging 과정에서 거의 발생하는 것 같다.
파이썬말고 다른 언어로 만들어서 추가해보던지 아니면 최적화를 더 찾아보는 것이 해답일 것 같다.