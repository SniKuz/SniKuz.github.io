---
title: "LeetCode - Rotate Image(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/rotate-image/)
+ You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

+ You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.
---
**Example**
```

```
---
+ 문제 1차 풀이
  1. 문제는 n x n 표를 오른쪽으로 회전할 때 모습. (i, j) -> (j, n-1-i)위치에 간다는 것을 알 수 있다.
  2. 문제가 2차원 배열이 아니라 배열 속 배열(들쭉날쭉 배열)이라 맞춰서 몇가지 추가가 있다.
---
```
//C#
public class Solution {
    public void Rotate(int[][] matrix) {
        int n = matrix.Length;
        int[][] tempMatrix = new int[n][];
        for(int i = 0; i < n; i++){
            tempMatrix[i] = new int[n];
        }
        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                tempMatrix[i][j] = matrix[i][j];
            }
        }
        
        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                matrix[j][n-1 -i] = tempMatrix[i][j];
            }
        }
    }
}
```
+ Runtime: 248 ms, faster than 38.10% of C# online submissions for Rotate Image.
+ Memory Usage: 30.8 MB, less than 84.22% of C# online submissions for Rotate Image.


---
+ 정리
  1. 배열 속 배열이라 2차원 배열처럼 사용하려하니 문제가 첫 for : 배열 내 배열 길이 선언(열), 두 번째 for : 복사, 세 번째 for : 위치변경
  2. 다른 알고리즘 공부를 진행하는데 코드를 좋게 써보려고 고민을 하다 보니 한 문제도 제대로 풀지를 못했다... 하루 한 문제 코드를 좋게 쓰는 방식으로 공부하도록 노력.