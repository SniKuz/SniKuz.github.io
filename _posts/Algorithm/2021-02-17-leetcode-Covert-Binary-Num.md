---
title: "Convert Binary Number in a Linked List to Integer(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/)
+ Given head which is a reference node to a singly-linked list. The value of each node in the linked list is either 0 or 1. The linked list holds the binary representation of a number.
+ Return the decimal value of the number in the linked list.
---
**Example**

```
Input: head = [1,0,1]
Output: 5
Explanation: (101) in base 2 = (5) in base 10
Input: head = [1,0,0,1,0,0,1,1,1,0,0,0,0,0,0]
Output: 18880
```

+ 문제 1차 풀이
  1. 문자열에 리스트 순회하며 값을 다 넣어준 뒤 이진수를 십진수로 변환


```
//C#
public class Solution {
    public int GetDecimalValue(ListNode head) {
        string result = "";
        int intResult = 0;
        while(head != null){
            result += head.val +"";
            head = head.next;
        }
        intResult += Convert.ToInt32(result, 2);
        return intResult;
    }
}
```
+ Runtime: 84 ms, faster than 94.19% of C# online submissions for Convert Binary Number in a Linked List to Integer.
+ Memory Usage: 24.8 MB, less than 65.12% of C# online submissions for Convert Binary Number in a Linked List to Integer.

