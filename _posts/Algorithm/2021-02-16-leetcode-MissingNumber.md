---
title: "LeetCode - Missing Number(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/missing-number/submissions/)
+ Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.
+ Follow up: Could you implement a solution using only O(1) extra space complexity and O(n) runtime complexity?
---
**Example**

```
Input: nums = [9,6,4,2,3,5,7,0,1]
Output: 8
Explanation: n = 9 since there are 9 numbers, so all numbers are in the range [0,9]. 8 is the missing number in the range since it does not appear in nums.
```

+ 문제 1차 풀이
  1. 


```
//C#
public class Solution {
    public int MissingNumber(int[] nums) {
        int result;
        Dictionary<int, int> dictionary = new Dictionary<int, int>();
        for(int i = 0; i < nums.Length; i++){
            dictionary.Add(nums[i], nums[i]);
        }
        for(result = 0; result<= nums.Length; result++){
            if(!dictionary.ContainsValue(result))
                return result;
        }
        return result;
    }
}
```
```
//다른 분들 코드

//가장 빠른 예
public class Solution {
    public int MissingNumber(int[] nums) 
    {
        var len = nums.Length;
        var expectedSum = len * (len + 1) / 2;
        var actual = 0;
        
        for(var i = 0; i < nums.Length; i++)
        {
            actual += nums[i];
        }
        
        return expectedSum - actual;
    }
}
//가장 공간 작은 예
public class Solution {
    public int MissingNumber(int[] nums) {
        var number = nums.Length;
        for(var i = 0; i < nums.Length; i++){
            number ^= i;
            number ^= nums[i];
        }
        return number;
    }
}
```
+ Runtime: 2324 ms, faster than 5.06% of C# online submissions for Missing Number.
+ Memory Usage: 36.8 MB, less than 5.18% of C# online submissions for Missing Number.

배운점
1. O(n)시간 복잡도, O(1)의 공간 복잡도. 위 코드는 시간 복잡도는 n인데 (2n) 공간 복잡도도 n.. 음.
2. 속도와 메모리 둘다 매우 비효율적인데 다른 분들의 코드도 확인하고 비교하며 고쳐봐야겠다.