---
title: "LeetCode - Palindrome Number(easy)"
excerpt: "Palindrome Number"
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/palindrome-number/submissions/)
+ Given an integer x, return true if x is palindrome integer.

+ An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.

---
**Example**
```
Input: x = 121
Output: true

Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```
---
+ 문제 1차 풀이
  1. 문제에서 문자열로 풀라는 느낌을 받았지만 정수형으로 푸는게 더 빠를까? 싶어서 시도 -> 비효율적인 것 같음
  2. 평범하게 문자열로 풀기로 진행 -> Clear
```
//C#
public class Solution {
    public bool IsPalindrome(int x) {
			if(x < 0) return false;

			string strX = x.ToString();

			for(int i = 0; i < strX.Length/2; i++){
				if(strX[i] != strX[strX.Length -1 -i]) return false;
			}
			return true;
    }
}
```
+ Runtime: 56 ms, faster than 93.80% of C# online submissions for Palindrome Number.
+ Memory Usage: 17.1 MB, less than 33.62% of C# online submissions for Palindrome Number.

---
배운점
  1. 1학년 때 봤던 문제인데 오랜만에 봤다. 역시 Easy문제인지 더 공부가 필요. 푸는데 얼마 안걸린걸 보니 역시 자주 접해봐야겠다.