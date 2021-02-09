---
title: "LeetCode - Median of Two Sorted Arrays(medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/longest-palindromic-substring/submissions/)
+ Given a string s, return the longest palindromic substring in s.
---
**Example**
```
Input: s = "babad"
Output: "bab"
Note: "aba" is also a valid answer.

Input: s = "cbbd"
Output: "bb"

Input: s = "ac"
Output: "a"

Input: s = "a"
Output: "a"
```
---
+ 문제 1차 풀이
  1. 시작 char i 나머지 진행 char j로 char을 포함하면서 Palindrom이면 길이 저장하며 문자열을 다 도는 방식 -> 시간초과에러
  2. Solution 코드를 찾아서 확인...
```
//C#
public class Solution {
    public string LongestPalindrome(string s) {
        string result ="";
        string tempStr="";
        for(int i = 0; i<s.Length; i++){
            tempStr = s[i].ToString();
            for(int j=i+1; j<s.Length; j++){
                tempStr+=s[j];
                if(Palindrom(tempStr)){
                    result = result.Length > tempStr.Length ? result : tempStr;
                }
            }
        }
        return result = result.Length == 0 ? s[0].ToString() : result;
    }

    public bool Palindrom(string s){
        for(int i = 0; i< s.Length/2; i++){
            if(s[i] != s[s.Length-i-1]) return false;
        }
        return true;
    }
}
```
//C# Solution
    public string LongestPalindrome(string s) {
        int len = s.Length, start = 0, maxLength = 0, i = 0, left = 0, right = 0;
        while(i < len){
            left = i - 1;
            right = i + 1;
            while(right < len && s[right] == s[i]) right++;
            i = right;
            while(left>=0 && right < len && s[right] == s[left]){
                left--;
                right++;
            }
            if (maxLength < right - left - 1){
                maxLength = right - left - 1;
                start = left + 1;
            }
        }
        return s.Substring(start, maxLength);
    }
}
```
+ Runtime: 80 ms, faster than 99.53% of C# online submissions for Longest Palindromic Substring.
+ Memory Usage: 24.5 MB, less than 85.06% of C# online submissions for Longest Palindromic Substring.


---
배운점
  1.  기존 모든 경우를 이중 for문으로 찾는게 비효율적이고 시간이 오래걸리는 반면 Solution은 양 옆을 확인하면서 기존 코드처럼 비효율적인 반복이 없는 것 같다.
	2. 기존 코드도 시간을 단축시키거나 변형하면 사용할 수 있을지 고민이 필요.