---
title: "Unique Paths(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/unique-paths/)
+ A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

+ The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

+ How many possible unique paths are there?
---
**Example**

```
Input: m = 3, n = 7
Output: 28
Input: m = 3, n = 2
Output: 3
```

+ 문제 1차 풀이
  1. 시작점에서 가로, 세로는 직진이니 1. 내부 [1,1]~[n,n]은 이전 경로의 합


```
//C#
public class Solution {
    public int UniquePaths(int m, int n) {
        int[,] dp = new int[m, n];
        for(int i = 0; i < m; i++){
            dp[i, 0] = 1;
        }
        for(int i = 0; i < n; i++){
            dp[0, i] = 1;
        }
        for(int i = 1; i < m; i++)
            for(int j = 1; j < n; j++){
                dp[i, j] = dp[i-1, j] + dp[i, j-1];
            }
        return dp[m-1, n-1];
    }
}
```
+ Runtime: 36 ms, faster than 93.84% of C# online submissions for Unique Paths.
+ Memory Usage: 15.2 MB, less than 80.82% of C# online submissions for Unique Paths.


