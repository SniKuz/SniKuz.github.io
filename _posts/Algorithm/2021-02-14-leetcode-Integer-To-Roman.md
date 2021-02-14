---
title: "LeetCode - Integer To Raman(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/integer-to-roman/submissions/)
+ Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000

+ For example, 2 is written as II in Roman numeral, just two one's added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.
---
**Example**
```
Input: num = 58
Output: "LVIII"
Explanation: L = 50, V = 5, III = 3.
```
---
+ 문제 1차 풀이
  1. 딕셔너리로 푸는 방법을 고민해 보다가 그냥 직관적으로 작성.
---
```
//C#
public class Solution {
    public string IntToRoman(int num) {
        string result = "";
        while(num > 0){
            if(num >= 1000){
                num -= 1000;
                result += "M";
            }
            else if(num >= 900){
                num -= 900;
                result += "CM";
            }
            else if(num >= 500){
                num -= 500;
                result += "D";
            }
            else if(num >= 400){
                num -= 400;
                result += "CD";
            }
            else if(num >= 100){
                num -= 100;
                result += "C";
            }
            else if(num >= 90){
                num -= 90;
                result += "XC";
            }
            else if(num >= 50){
                num -= 50;
                result += "L";
            }
            else if(num >= 40){
                num -= 40;
                result += "XL";
            }
            else if(num >= 10){
                num -= 10;
                result += "X";
            }
            else if(num >= 9){
                num -= 9;
                result += "IX";
            }
            else if(num >= 5){
                num -= 5;
                result += "V";
            }
            else if(num >= 4){
                num -= 4;
                result += "IV";
            }
            else if(num >= 1){
                num -= 1;
                result += "I";
            }
        }
        return result;
    }
}
```
//Solution C#. RunTime 빠른거 다른분거
public class Solution {
    public string IntToRoman(int num) {
    
        var maps = new RomanToInt[]{
            new RomanToInt("M",1000),
            new RomanToInt("CM",900),
            new RomanToInt("D",500),
            new RomanToInt("CD",400),
            new RomanToInt("C",100),
            new RomanToInt("XC",90),
            new RomanToInt("L",50),
            new RomanToInt("XL",40),
            new RomanToInt("X",10),
            new RomanToInt("IX",9),
            new RomanToInt("V",5),
            new RomanToInt("IV",4),
            new RomanToInt("I",1),            
        };
        var retString = new StringBuilder();
        
        for(var i = 0; i < maps.Length; i++) 
        {
            var valToCheck = maps[i];
            
            var count = num / valToCheck.Value;
            num = num % valToCheck.Value;
            for (var j = 0; j < count; j++) 
            {
                retString.Append(valToCheck.Roman);
            }
        }
        
        return retString.ToString();
    }
    
    
}

public class RomanToInt {
    
    public string Roman {get;}
    public int Value {get;}
    
    public RomanToInt(string roman, int val)
    {
        Roman = roman;
        Value = val;        
    }
}
```
+ Runtime: 132 ms, faster than 29.63% of C# online submissions for ZigZag Conversion.
+ Memory Usage: 26.9 MB, less than 82.02% of C# online submissions for ZigZag Conversion.

---
배운점
	1. 어떤 자료의 형태를 고민하는게 역시 우선적인 부분인 것 같다. 속도 차이가 많이 나는구나...