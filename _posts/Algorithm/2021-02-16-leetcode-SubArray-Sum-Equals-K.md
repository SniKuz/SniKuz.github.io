---
title: "LeetCode - SubArray Sum Equals K(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/subarray-sum-equals-k/)
+ Given an array of integers nums and an integer k, return the total number of continuous subarrays whose sum equals to k.
---
**Example**

```
Input: nums = [1,1,1], k = 2
Output: 2
Input: nums = [1,2,3], k = 3
Output: 2
```

+ 문제 1차 풀이
  1. 이중 for문으로 잘라서 하위 배열이 k와 같을 때 개수 증가


```
//C#
public class Solution {
    public int SubarraySum(int[] nums, int k) {
        int result = 0;
        for(int i = 0; i<nums.Length; i++){
            int temp = 0;
            for(int j = i; j<nums.Length; j++){
                temp += nums[j];
                if(temp == k) result++;
            }
        }
        return result;
    }
}
```
+ Runtime: 2108 ms, faster than 21.76% of C# online submissions for Subarray Sum Equals K.
+ Memory Usage: 32.7 MB, less than 99.34% of C# online submissions for Subarray Sum Equals K.

