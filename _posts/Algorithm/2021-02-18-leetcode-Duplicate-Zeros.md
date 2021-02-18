---
title: "Duplicate Zeros(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/duplicate-zeros/)
+ Given a fixed length array arr of integers, duplicate each occurrence of zero, shifting the remaining elements to the right.
+ Note that elements beyond the length of the original array are not written.
+ Do the above modifications to the input array in place, do not return anything from your function.
---
**Example**

```
Input: [1,0,2,3,0,4,5,0]
Output: null
Explanation: After calling your function, the input array is modified to: [1,0,0,2,3,0,0,4]
Input: [1,2,3]
Output: null
Explanation: After calling your function, the input array is modified to: [1,2,3]
```

+ 문제 1차 풀이
  1. 이중 for문으로 뒤에서부터 돌려주기
```
//C#
public class Solution {
    public void DuplicateZeros(int[] arr) {
        for(int i = arr.Length-1; 0 <= i; i--){
            if(arr[i] == 0){
                for(int j = arr.Length-1; i < j; j--){
                    arr[j] = arr[j-1];
                }
            }
        }
    }
}
```
+ Runtime: 264 ms, faster than 47.34% of C# online submissions for Duplicate Zeros.
+ Memory Usage: 33.3 MB, less than 46.38% of C# online submissions for Duplicate Zeros.