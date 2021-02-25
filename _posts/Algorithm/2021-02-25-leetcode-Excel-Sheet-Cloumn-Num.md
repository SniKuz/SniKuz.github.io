---
title: "Excel Sheet Column Number(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/excel-sheet-column-number/)
+ Given a column title as appear in an Excel sheet, return its corresponding column number.
+   A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
**Example**

```
Input: "AB"
Output: 28
Input: "ZY"
Output: 701
```

```
//Python
class Solution(object):
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        result = 0
        lenStr = len(s)-1
        alphabet = {'A':1, 'B':2, 'C':3,'D':4,
                    'E':5, 'F':6, 'G':7,'H':8,
                    'I':9, 'J':10, 'K':11,'L':12,
                    'M':13, 'N':14, 'O':15,'P':16,
                    'Q':17, 'R':18, 'S':19,'T':20,
                    'U':21, 'V':22, 'W':23,'X':24,
                    'Y':25, 'Z':26}
        for i in range(0, len(s)):
            result += alphabet[s[i]] * pow(26, lenStr)
            lenStr -= 1
        return result
```
+ Runtime: 24 ms, faster than 44.83% of Python online submissions for Excel Sheet Column Number.
+ Memory Usage: 13.5 MB, less than 57.76% of Python online submissions for Excel Sheet Column Number.


---