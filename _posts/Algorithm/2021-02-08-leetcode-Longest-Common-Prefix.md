---
title: "LeetCode - Longest Common Prefix (easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/longest-common-prefix/)
+ Write a function to find the longest common prefix string amongst an array of strings. If there is no common prefix, return an empty string "".

---
**Example**
```
Input: strs = ["flower","flow","flight"]
Output: "fl"

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```
---
+ 문제 1차 풀이
  1. 처음에 단순 for로 이전, 다음 단어에 대한 비교 -> 몇 케이스에 따라 에러 발생
  2. 다른 사람의 예시 확인. foreach로 파이썬 for in처럼 깔끔하게 하는 방식이 좋다 생각.
```
//C#
public class Solution {
    public string LongestCommonPrefix(string[] strs) {
        if (strs.Length == 0 || Array.IndexOf(strs, "") != -1)
            return "";
        string res = strs[0];
        int i = res.Length;
        foreach (string word in strs) {
            int j = 0;
            foreach (char c in word) {
                if (j >= i || res[j] != c)
                    break;
                j += 1;
            }
            i = Math.Min(i, j);
        }
        return res.Substring(0, i);
    }
}
```
+ Runtime: 96 ms, faster than 91.11% of C# online submissions for Longest Common Prefix.
+ Memory Usage: 25.2 MB, less than 68.99% of C# online submissions for Longest Common Prefix.

---
배운점
  1. foreach와 같은 방식으로 깔끔하게 진행할 수 있는데, 평소 자주 사용을 안해서 그런지 생각을 못했다. 다양하게 다 경험해보는 것은 중요하다 생각한다.