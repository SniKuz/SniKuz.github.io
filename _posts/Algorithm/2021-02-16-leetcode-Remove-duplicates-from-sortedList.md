---
title: "LeetCode - Remove Duplicates from Sorted List(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)
+ Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.
---
**Example**

```
Input: head = [1,1,2]
Output: [1,2]
Input: head = [1,1,2,3,3]
Output: [1,2,3]
```

+ 문제 1차 풀이
  1. 동일한것이 아닐때까지 스킵 후 연결, 마지막 부분에서는 끊기.


```
//C#
public class Solution {
    public ListNode DeleteDuplicates(ListNode head) {
        if(head == null || head.next == null) return head;
        ListNode beforeTemp = head;
        for(ListNode temp = head; temp != null; temp = temp.next){
            if(beforeTemp.val < temp.val){
                beforeTemp.next = temp;
                beforeTemp = beforeTemp.next;
            }
        }
        beforeTemp.next = null;
        return head;
    }
}
```
+ Runtime: 88 ms, faster than 97.03% of C# online submissions for Remove Duplicates from Sorted List.
+ Memory Usage: 26.5 MB, less than 73.23% of C# online submissions for Remove Duplicates from Sorted List.
