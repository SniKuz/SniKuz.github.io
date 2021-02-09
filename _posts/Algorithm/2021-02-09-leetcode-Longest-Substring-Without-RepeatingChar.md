---
title: "LeetCode - Longest Substring Without Repeating Characters(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
+ Given a string s, find the length of the longest substring without repeating characters.

---
**Example**
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

Input: s = ""
Output: 0
```
---
+ 문제 1차 풀이
  1. foreach로 하나 씩 꺼내서 tempStr에 없으면 추가, 있으면 초기화 하는 방식으로 진행
```
//C#
public class Solution {
    public int LengthOfLongestSubstring(string s) {
        int result = 0;
        string tempStr = "";
        int whereIsSame = 0;
        foreach (var item in s)
        {
            bool isSub = true;
            for(int i = 0; i < tempStr.Length; i++){
                if(tempStr[i] == item){
                    isSub = false;
                    whereIsSame = i;
                }
            }
            if(isSub) tempStr += item;
            else{
                tempStr = tempStr.Substring(whereIsSame+1) + item;
                whereIsSame = 0;
            }
            result = result > tempStr.Length ? result : tempStr.Length;
        }
        return result;
    }
}
```
//Solution -> 참고. RunTime 60ms
public class Solution {
    public int LengthOfLongestSubstring(string s) {
        int[] index = new int[128];
        int i=0, ans = 0;
        for (int j=0; j<s.Length; j++){
            i = Math.Max(index[s[j]], i);
            ans = Math.Max(ans, j-i+1);
            index[s[j]] = j+1;
        }
        
        return ans;
    }
}
```
+ Runtime: 96 ms, faster than 53.45% of C# online submissions for Longest Substring Without Repeating Characters.
+ Memory Usage: 26.5 MB, less than 40.81% of C# online submissions for Longest Substring Without Repeating Characters.


---
배운점
  1. 좀 더 고민해서 방식을 발전시켜보려 했지만, 더 깔끔하고 빠른 코드를 잘 살펴봐야겠다.
	2. 아스키코드를 떠올려서 저런 방식으로 간단하게 관리하는 방식으로 한 것이 매우 인상적이었다...