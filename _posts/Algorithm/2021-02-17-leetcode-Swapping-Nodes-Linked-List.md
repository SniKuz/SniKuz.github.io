---
title: "Swapping Nodes in a Linked List(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/)
+ You are given the head of a linked list, and an integer k.
+ Return the head of the linked list after swapping the values of the kth node from the beginning and the kth node from the end (the list is 1-indexed).
---
**Example**

```
Input: head = [1,2], k = 1
Output: [2,1]
Input: head = [7,9,6,6,7,8,3,0,9,5], k = 5
Output: [7,9,6,6,8,7,3,0,9,5]
```

+ 문제 1차 풀이
  1. 리스트 총 길이 체크
  2. 2개의 임시 리스트 노드를 자리를 바꿀 위치로 배치(for 문 2개)
  3. 값 변경
```
//C#
public class Solution {
    public ListNode SwapNodes(ListNode head, int k) {
        int len = 0;
        ListNode tempK = head;
        while(tempK != null){
            len++;
            tempK=tempK.next;
        }
        Console.WriteLine(len);
        
        tempK = head;
        ListNode tempBackK = head;
        for(int i = 1; i < k; i++)
            tempK = tempK.next;
        for(int i = 1; i <len-k+1; i++)
            tempBackK = tempBackK.next;
        int tempInt = tempK.val;
        tempK.val = tempBackK.val;
        tempBackK.val = tempInt;
        return head;
    }
}
```
+ Runtime: 344 ms, faster than 87.33% of C# online submissions for Swapping Nodes in a Linked List.
+ Memory Usage: 53 MB, less than 85.07% of C# online submissions for Swapping Nodes in a Linked List.
