---
title: "Flipping an Image(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/flipping-an-image/)
+ Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.
+ To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].
+ To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].
**Example**

```
Input: [[1,1,0],[1,0,1],[0,0,0]]
Output: [[1,0,0],[0,1,0],[1,1,1]]
Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]
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
+ Runtime: 40 ms, faster than 40.89% of Python online submissions for Flipping an Image.
+ Memory Usage: 13.3 MB, less than 94.94% of Python online submissions for Flipping an Image.
---