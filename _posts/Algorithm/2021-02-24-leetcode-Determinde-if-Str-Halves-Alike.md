---
title: " Determine if String Halves Are Alike(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/determine-if-string-halves-are-alike/)
+ You are given a string s of even length. Split this string into two halves of equal lengths, and let a be the first half and b be the second half.
+ Two strings are alike if they have the same number of vowels ('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'). Notice that s contains uppercase and lowercase letters.
+ Return true if a and b are alike. Otherwise, return false.nums.
**Example**
```
Input: s = "textbook"
Output: false
Explanation: a = "text" and b = "book". a has 1 vowel whereas b has 2. Therefore, they are not alike.
Notice that the vowel o is counted twice.
```

```
//Python
class Solution(object):
    def halvesAreAlike(self, s):
        """
        :type s: str
        :rtype: bool
        """
        left = s[0:len(s)/2]
        leftCnt = 0
        right = s[len(s)/2:]
        rightCnt = 0
        aeiou = ['a','e','i','o','u','A','E','I','O','U']
        for i in left:
            if i in aeiou:
                leftCnt += 1
        for i in right:
            if i in aeiou:
                rightCnt += 1
        return leftCnt == rightCnt
```
+ Runtime: 24 ms, faster than 77.75% of Python online submissions for Determine if String Halves Are Alike.
+ Memory Usage: 13.7 MB, less than 13.57% of Python online submissions for Determine if String Halves Are Alike.

---