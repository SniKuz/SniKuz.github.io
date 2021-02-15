---
title: "LeetCode - Search Insert Position(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/search-insert-position/submissions/)
+ Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
---
**Example**

```
Input: nums = [1,3,5,6], target = 5
Output: 2
Input: nums = [1,3,5,6], target = 7
Output: 4
Input: nums = [1,3,5,6], target = 0
Output: 0
Input: nums = [1], target = 0
Output: 0
```

+ 문제 1차 풀이
  1. 


```
//C#
public class Solution {
    public int SearchInsert(int[] nums, int target) {
        int result = 0;
        for(int i = 0; i<nums.Length; i++){
            if(nums[i] >= target){
                result = i;
                break;
            }
            if(i >= nums.Length-1) result = nums.Length;
        }
        return result;
    }
}
```
//Solution C#. RunTime 빠른거 다른분거

```
+ Runtime: 88 ms, faster than 94.54% of C# online submissions for Search Insert Position.
+ Memory Usage: 25.3 MB, less than 32.46% of C# online submissions for Search Insert Position.

배운점
	1. break로 중간에 끊어서 속도가 빠른것 같지만 좋은 방식인지는 궁금증이 생긴다.