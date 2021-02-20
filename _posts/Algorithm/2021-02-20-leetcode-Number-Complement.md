---
title: "Number Complement(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/number-complement/)
+ Given a positive integer num, output its complement number. The complement strategy is to flip the bits of its binary representation.
**Example**

```
Input: num = 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
```

```
//Python
class Solution(object):
    def findComplement(self, num):
        """
        :type num: int
        :rtype: int
        """
        temp = "".join(bin(num))
        print(temp)
        result = ""
        for i in range(2, len(temp)):
            result += '1' if temp[i] == '0' else '0'
        return int(result, 2)
```
+ Runtime: 16 ms, faster than 71.07% of Python online submissions for Number Complement.
+ Memory Usage: 13.4 MB, less than 40.10% of Python online submissions for Number
---