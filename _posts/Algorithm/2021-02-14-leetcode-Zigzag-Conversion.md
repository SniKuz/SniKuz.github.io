---
title: "LeetCode - Zigzag Conversion(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/zigzag-conversion/submissions/)
+ The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);
---
**Example**
```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:
P     I    N
A   L S  I G
Y A   H R
P     I

Input: s = "A", numRows = 1
Output: "A"
```
---
+ 문제 1차 풀이
  1. 0->1->2..numRows->numRows-1->...0->1->2->.. 을 s의 길이까지 진행
  2. 첫 도전 -> Error numRows가 1일때 RunTimeError System.IndexOutOfRangeException: Index was outside the bounds of the array. -> 맨 위에 numRows == 1일때 추가
---
```
//C#
public class Solution {
    public string Convert(string s, int numRows) {
        if(numRows == 1) return s;
        string[] converStr = new string[numRows];
        string result = "";
        int level = 0;
        bool isReturn = false;
        for(int i = 0; i < s.Length; i++){
            converStr[level] += s[i];

            if(level >= numRows-1 || level <= 0) isReturn = !isReturn; 

            if(isReturn) level++;
            else level--;
        }
        for(int i = 0; i < numRows; i++){
            result += converStr[i];
        }
        return result;
    }
}
```
+ Runtime: 132 ms, faster than 29.63% of C# online submissions for ZigZag Conversion.
+ Memory Usage: 26.9 MB, less than 82.02% of C# online submissions for ZigZag Conversion.


---