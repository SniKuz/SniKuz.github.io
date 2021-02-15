---
title: "find-first-and-last-position-of-element-in-sorted-array(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/submissions/)
+ Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

+ If target is not found in the array, return [-1, -1].

+ Follow up: Could you write an algorithm with O(log n) runtime complexity?
---
**Example**

```
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
Input: nums = [], target = 0
Output: [-1,-1]
```

+ 문제 1차 풀이
  1. for을 이용해 첫 시작 체크. 만약 없으면 마무리. 이후 2번째 for로 first position 부터 체크


```
//C#
public class Solution {
    public int[] SearchRange(int[] nums, int target) {
        int[] result = new int[2] {-1, -1};
        for(int i = 0; i < nums.Length; i++)
        {
            if(nums[i] == target){
                result[0] = i;
                break;
            }
        }
        if(result[0] == -1) return result;

        for(int i = result[0]; i<nums.Length; i++){
            if(nums[i] == target){
                result[1] = i;
            }
        }
        return result;
    }
}
```
//Solution C#. RunTime 빠른거 다른분거

```
+ Runtime: 240 ms, faster than 85.82% of C# online submissions for Find First and Last Position of Element in Sorted Array.
+ Memory Usage: 32.7 MB, less than 54.26% of C# online submissions for Find First and Last Position of Element in Sorted Array.

배운점
	1. 이전 문제처럼 break로 중간에 끊어서 속도가 빠른것 같지만 좋은 방식인지는 궁금증이 생긴다.