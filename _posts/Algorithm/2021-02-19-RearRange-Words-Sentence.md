---
title: "Rearrange Words in a Sentence(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/rearrange-words-in-a-sentence/)
+ Given a sentence text (A sentence is a string of space-separated words) in the following format:
+ First letter is in upper case.
+ Each word in text are separated by a single space.
+ Your task is to rearrange the words in text such that all words are rearranged in an increasing order of their lengths. If two words have the same length, arrange them in their original order.
+ Return the new text following the format shown above.---
**Example**

```
Input: text = "Keep calm and code on"
Output: "On and keep calm code"
Explanation: Output is ordered as follows:
"On" 2 letters.
"and" 3 letters.
"keep" 4 letters in case of tie order by position in original text.
"calm" 4 letters.
"code" 4 letters.
```

```
//Python
class Solution(object):
    def arrangeWords(self, text):
        """
        :type text: str
        :rtype: str
        """
        text = text.lower()
        textSplit = text.split()
        textSplit.sort(key=len)
        result = ' '.join(textSplit)
        result = result[0].upper() + result[1:]
        return result
```
+ Runtime: 24 ms, faster than 98.44% of Python online submissions for Rearrange Words in a Sentence.
+ Memory Usage: 17.4 MB, less than 31.25% of Python online submissions for Rearrange
---
알고리즘 풀 때 파이썬이 많이 쓰인다고도 해서 한 번 사용해 봤는데 확실히 왜 더 편하다는지 알겠다. 하지만 파이썬도 그렇고 C#, C++도 그렇고 기본적인 문법과 기본 라이브러리에 대한 지식이 부족한 점 + @에서 아.. 확실히 게임 개발에 쓰이는 C++, C#과 3, 4학년 시기 캡스톤으로 해보고 싶은 분야에 자주 쓰이는 파이썬 이 3개는 능숙하게 사용할 수 있게 공부해야겠다.