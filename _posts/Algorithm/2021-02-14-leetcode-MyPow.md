---
title: "LeetCode - MyPow(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/powx-n/submissions/)
+ Implement pow(x, n), which calculates x raised to the power n (i.e. xn).
---
**Example**

```
Input: x = 2.00000, n = 10
Output: 1024.00000

Input: x = 2.10000, n = 3
Output: 9.26100

Input: x = 2.00000, n = -2
Output: 0.25000
Explanation: 2-2 = 1/22 = 1/4 = 0.25

Input: x = 2.00000, n = -2147483648
Output: 0
```

+ 문제 1차 풀이
  1. while로 양/음수일 때 각각 반복문을 진행 -> Error : x = 0.000001, n = 2147483647  Time Limited Exceed
  2. 재귀방식으로 변경. n%2==0, 1일때에 각각 재귀방식으로 /2씩 줄이며 진행 ->  x가 2, n이 -2147483648일 때  output이 Infinity가 나왔는데 문제 답은 0
  3. x가 Infinity일때 return 0 추가.


```
//C#
public class Solution {
    public double MyPow(double x, int n) {
        if(x == double.PositiveInfinity || x == double.NegativeInfinity) return 0;
        if( n == 0 ) return 1;
        if(n < 0){
            x = 1/x;
            n *= -1;
        }
        if(n%2 == 0) return MyPow(x*x, n/2);
        else return MyPow(x*x, n/2) * x;
    }
}
```
//Solution C#. RunTime 빠른거 다른분거
public class Solution {
    public double MyPow(double x, int n) {
        if(n == 0 )
            return 1; 
        
        double t = MyPow( x, n/2); 
        
        if(n % 2 != 0) 
            return n < 0 ? 1 / x * t * t : x * t * t; 
        
        else return t * t ; 
    }
}
```
+ Runtime: 48 ms, faster than 64.31% of C# online submissions for Pow(x, n).
+ Memory Usage: 15.8 MB, less than 19.45% of C# online submissions for Pow(x, n).

배운점
	1. 재귀방식으로 변경은 좋았으나 조금 더 구체화를 했으면 좋았을 것같다.