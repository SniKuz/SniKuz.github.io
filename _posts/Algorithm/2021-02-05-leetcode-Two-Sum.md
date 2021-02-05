---
title: "LeetCode - Two Sum(easy)"
excerpt: "Two Sum"
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/two-sum/)
+ Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

+ You may assume that each input would have exactly one solution, and you may not use the same element twice.

+ You can return the answer in any order.

---
**Example 1:**
```
Input: nums = [2, 7, 11, 15], target = 9
Output: [0, 1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```
---
+ 문제 1차 풀이
  1. 이중 for문으로 일부 확인해서 풀기 -> 이미 사용한 위치는 쓰면 안되서 wrong answer
  2. 이미 사용한 위치 사용 X -> 음수 고려를 안했어서 wrong answer
  3. 그냥 이중 for문으로 일일이 확인해서 풀기 -> Clear
```
//C#
public class Solution {
    public int[] TwoSum(int[] nums, int target) {
        int arrayLen = nums.Length;
				int[] result = new int[2];
				int fNum;
				for(int i = 0; i<arrayLen-1; i++){
					fNum = nums[i];
					for(int j = i+1; j<arrayLen; j++){
						if(fNum + nums[j] == target){
							result[0] = i;
							result[1] = j;
						}
					}
				}
				return result;
		}
}
```
+ Runtime: 244 ms, faster than 56.50% of C# online submissions for Two Sum.
+ Memory Usage: 31.9 MB, less than 22.05% of C# online submissions for Two Sum.

---
배운점
  1. 문제를 너무 안 읽고 이해를 못하는 것 같다. 음수도 당연히 있어야 하는건데 고민을 더 하자.
  2. C#을 유니티로 활용만 좀 해보는걸로 해서 유니티에서 간단하게 쓰는건 알아도 제대로 알지 못한다. 제대로 공부가 필요한 것 같다.
  3. 처음에 이중 for문은 비효율적인 것 같아서 다른 방식을 고민을 많이 해봤지만 떠올르지가 않는다... 더 고민을 해봐야겠다. 
  4. leetcode가 난이도별로 되어있고 다른 사람들 의견이나 설명이 많은 것 같아서 + 표본 정리를 한 눈에 볼 수 있을 것 같아서 먼저 이걸로 해보기로 결정했다.

