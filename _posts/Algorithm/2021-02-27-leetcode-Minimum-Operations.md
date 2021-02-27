---
title: "Minimum Operations to Reduce X to Zero(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/)
+ You are given an integer array nums and an integer x. In one operation, you can either remove the leftmost or the rightmost element from the array nums and subtract its value from x. Note that this modifies the array for future operations.
+ Return the minimum number of operations to reduce x to exactly 0 if it's possible, otherwise, return -1.
**Example**

```
Input: nums = [1,1,4,2,3], x = 5
Output: 2
Explanation: The optimal solution is to remove the last two elements to reduce x to zero.
```

```
class Solution(object):
    def minOperations(self, nums, x):
        """
        :type nums: List[int]
        :type x: int
        :rtype: int
        """
        def recursiveCheck(nums, x, cnt):
            if (nums[0] > x and nums[-1] > x):
                return 987654321
            cnt += 1
            if nums[0] == x:
                return cnt
            elif nums[-1] == x:
                return cnt
            else:
                return min(recursiveCheck(nums[1:], x-nums[0], cnt),
                recursiveCheck(nums[:-1], x-nums[-1], cnt))
        target = sum(nums) - x
        if target < 0: return -1
        if target == 0: return len(nums)
        result = recursiveCheck(nums, x, 0)
        return result
#다른분의 Solution
class Solution:
    def minOperations(self, nums, x):
        target = sum(nums) - x
        n = len(nums)

        if target < 0: return -1
        if target == 0: return n

        left = 0;
        cur_sum = 0;
        n_target = -1

        for i in range(n):
            if cur_sum < target:
                cur_sum += nums[i]
            while cur_sum >= target:
                if cur_sum == target:
                    n_target = max(n_target, i - left + 1)
                cur_sum -= nums[left]
                left += 1

        return n - n_target if n_target != -1 else -1
```
+ Runtime: 1012 ms, faster than 82.52% of Python online submissions for Minimum Operations to Reduce X to Zero.
+ Memory Usage: 24.4 MB, less than 75.40% of Python online submissions for Minimum Operations to Reduce X to Zero
---
1. 재귀함수는 역시 Time Limit이 자주 발생한다. 좀 더 깊은 생각을 해야한다.
2. 2번 제출을 해 봤는데 Runtime이 다른 것을 보니 서버에서 돌리는 시간의 차이가 꽤 유의미하게 발생하는 것 같다. 메모리의 경우는 변동이 없는 것을 보아 준일하다.
3. 2번째 문제 푸는 방식은 이 배열의 총 합 - 구해야 하는 값을 가진 SubArray를 찾아, 그 SubArray의 양 옆에 존재하는 수가 정답이라는 방식으로 푼 것 같다. 기존 문제를 좀 더 직관적이고 쉽게 변형하는 방식이 인상적이다.