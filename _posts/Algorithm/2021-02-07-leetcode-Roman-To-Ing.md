---
title: "LeetCode - Roman to Integer(easy)"
excerpt: "Roman to Integer"
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/roman-to-integer/)
+ For example, 2 is written as II in Roman numeral, just two one's added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V II.

---
**Example**
```
```
---
+ 문제 1차 풀이
  1. string s를 for문에 넣어서 switch로 다 돌리며, for 문이 터질것 때문에 i==0일 경우 제한 걸어두고 끝냈다.
```
//C#
case 'M':
						if(i == 0) result += 1000;
						else if(s[i-1] == 'C') result += 800;
						else result += 1000;
						break;
```
+ Runtime: 92 ms, faster than 62.40% of C# online submissions for Roman to Integer.
+ Memory Usage: 26.7 MB, less than 6.98% of C# online submissions for Roman to Integer.

---
배운점
  1. 코드가 많이 더럽고 데이터 형식을 더 유용히 써야한다... 다른 사람들의 예시를 살펴봤는데 보통 딕셔너리로 만들어둔 후 코드로 깔끔하게 해결을 한 경우가 있던데 switch로 일일이 써놓은 게 너무 안좋다. 쉴까하다 대충 빨리 했지만 할 때 제대로 코드를 고민을 오래하는 습관을 꾸준히 만들어가야겠다.
