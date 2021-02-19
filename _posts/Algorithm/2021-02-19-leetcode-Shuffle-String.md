---
title: "Shuffle String(easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/shuffle-string/)
+ Given a string s and an integer array indices of the same length.
+ The string s will be shuffled such that the character at the ith position moves to indices[i] in the shuffled string.
+ Return the shuffled string.
---
**Example**

```
Input: s = "abc", indices = [0,1,2]
Output: "abc"
Explanation: After shuffling, each character remains in its position.
Input: s = "aaiougrt", indices = [4,0,2,6,7,3,1,5]
Output: "arigatou"
```

```
//Python
class Solution(object):
    def restoreString(self, s, indices):
        """
        :type s: str
        :type indices: List[int]
        :rtype: str
        """
        result = [''] * len(s)
        cnt = 0
        for i in indices:
            result[i] = s[cnt]
            cnt += 1
        result = ''.join(result)
        return result
```
+ Runtime: 36 ms, faster than 87.85% of Python online submissions for Shuffle String.
+ Memory Usage: 13.4 MB, less than 69.33% of Python online submissions for Shuffle String

