---
title: "Swapping Nodes in a Linked List(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/single-number-iii/)
+ Given an integer array nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once. You can return the answer in any order.
+ Follow up: Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?
---
**Example**

```
Input: nums = [1,2,1,3,2,5]
Output: [3,5]
Explanation:  [5, 3] is also a valid answer.
Input: nums = [-1,0]
Output: [-1,0]
```

+ 문제 1차 풀이
  1. 딕셔너리에 다 넣어서 2개 아닌 것만 만들어둔 배열에 넣어서 return
```
//C#
public class Solution {
    public int[] SingleNumber(int[] nums) {
        int[] result = new int[2];
        int cnt = 0;
        Dictionary<int, int> dic = new Dictionary<int, int>();
        for(int i = 0; i < nums.Length; i++){
            if(dic.ContainsKey(nums[i])) dic[nums[i]] += 1;
            else dic.Add(nums[i], 1);
        }
        foreach (KeyValuePair<int, int> item in dic)
        {
            if(item.Value < 2) result[cnt++] = item.Key;
        }
        return result;
    }
}
```
+ Runtime: 240 ms, faster than 83.65% of C# online submissions for Single Number III.
+ Memory Usage: 32.9 MB, less than 18.27% of C# online submissions for Single Number III.
