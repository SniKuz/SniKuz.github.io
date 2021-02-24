---
title: "Maximum Length of Subarray With Positive Product(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/maximum-length-of-subarray-with-positive-product/)
+ Given an array of integers nums, find the maximum length of a subarray where the product of all its elements is positive.
+ A subarray of an array is a consecutive sequence of zero or more values taken out of that array.
+ Return the maximum length of a subarray with positive product.
**Example**

```
Input: nums = [0,1,-2,-3,-4]
Output: 3
Explanation: The longest subarray with positive product is [1,-2,-3] which has a product of 6.
Notice that we cannot include 0 in the subarray since that'll make the product 0 which is not positive.
```

```
//Python
class Solution(object):
    def getMaxLen(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        result = 0
        for i in range(0, len(nums)):
            if nums[i] == 0: continue
            temp = 1
            for j in range(i, len(nums)):
                temp *= nums[j]
                if temp > 0:
                    result = result if j-i+1 < result else j-i+1
        return result
//Solution 다른 분거
def getMaxLen(self, nums):
    """
    :type nums: List[int]
    :rtype: int
    """
    n = len(nums)
    dp = [[0] * 2 for _ in range(n)]
    # dp[i][0] : max length of subarray ending with index i With positive product
    # dp[i][1] : max length of subarray ending with index i With negative product

    # Base case: when index is 0, only one number can be used
    if nums[0] > 0:
        dp[0][0] = 1

    if nums[0] < 0:
        dp[0][1] = 1

    res = dp[0][0]

    for i in range(1, n):
        cur = nums[i]

        if cur > 0:
            dp[i][0] = dp[i - 1][0] + 1
            if dp[i - 1][1] > 0:  # if previous negative subarray exists
                dp[i][1] = max(dp[i][1], dp[i - 1][1] + 1)
        if cur < 0:
            dp[i][1] = dp[i - 1][0] + 1
            if dp[i - 1][1] > 0:  # if previous negative subarray exists
                dp[i][0] = max(dp[i][0], dp[i - 1][1] + 1)

        res = max(res, dp[i][0])

    return res
```
+ Runtime: 824 ms, faster than 17.07% of Python online submissions for Maximum Length of Subarray With Positive Product.
+ Memory Usage: 38.3 MB, less than 9.76% of Python online submissions for Maximum Length of Subarray With Positive Product.
---
첫번째 코드의 경우 코드가 비효율적이라 Time Limit 에러가 생겼고, 밑에 코드를 참고.<br>최근 제대로 된 풀이를 못하는 것을 심각히 느껴서 독서 및 공부로 코드를 쓰기 전에 머리로 다 풀어보는 연습 필요