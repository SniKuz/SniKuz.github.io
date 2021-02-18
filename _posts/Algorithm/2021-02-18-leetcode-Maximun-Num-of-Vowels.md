---
title: "Maximum Number of Vowels in a Substring of Given Length(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)
+ Given a string s and an integer k.
+ Return the maximum number of vowel letters in any substring of s with length k.
+ Vowel letters in English are (a, e, i, o, u).
---
**Example**

```
Input: s = "abciiidef", k = 3
Output: 3
Explanation: The substring "iii" contains 3 vowel letters.
Input: s = "leetcode", k = 3
Output: 2
Explanation: "lee", "eet" and "ode" contain 2 vowels.
```

+ 문제 1차 풀이
  1. for문  속에 여러개의 for문으로 체크했으나 문자열이 1000줄이 넘으니 Time Limit Exceed
  2. 2중 for문으로 수정했으나 문자열이 10000줄이 넘으니 Time Limit Exceed
  3. for문을 하나로 줄이고 싶었으나 문자열을 효율적으로 짜를 방법을 생각을 못했고, 다른 분의 코드를 보고 확인.
```
//C#
public class Solution {
    public int MaxVowels(string s, int k) {
        int result = 0;
        int len = s.Length-k;
        for(int i = 0; i <= len; i++){
            int vowelTemp = 0;
            for(int j = i; j < i + k; j++){
                if(s[j] == 'a') vowelTemp++;
                else if(s[j] == 'e') vowelTemp++;
                else if(s[j] == 'i') vowelTemp++;
                else if(s[j] == 'o') vowelTemp++;
                else if(s[j] == 'u') vowelTemp++;
            }
            result = result>vowelTemp ? result : vowelTemp;
        }
        return result;
    }
}

//C# Solution
public int MaxVowels(string s, int k) 
{
	int maxVowels = 0;
	int vowels = 0;

	for(int i = 0; i < s.Length; i++)
	{
		vowels += ("aeiou".IndexOf(s[i]) >= 0 ? 1 : 0);

		if(i - k >= 0)
		{
			vowels -= ("aeiou".IndexOf(s[i - k]) >= 0 ? 1 : 0);                
		}

		maxVowels = Math.Max(maxVowels, vowels);
	}

	return maxVowels;
}
```
+ Runtime: 100 ms, faster than 60.00% of C# online submissions for Maximum Number of Vowels in a Substring of Given Length.
+ Memory Usage: 30.8 MB, less than 54.00% of C# online submissions for Maximum Number of Vowels in a Substring of Given Length.

---
느낀점
  1. 오늘 입대 전, 전역 전, 복학 전 대략적인 계획과 틀을 고민해보았는데 역시 아무리 봐도 언어에 기본적인 문법과 라이브러리 등을 너무 모른다. 이를 보완해야한다.
  2. 현재 생각으로는 C++, C# 과 같은 게임개발에 주로 쓰이는 언어와 데이터 마이닝을 위한 파이썬, 최소 3개에 대한 문법은 자유롭게 숙지해야 한다 생각한다. 