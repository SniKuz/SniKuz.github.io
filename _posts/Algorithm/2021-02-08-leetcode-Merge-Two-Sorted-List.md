---
title: "LeetCode - Merge Two Sorted Lists(easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/merge-two-sorted-lists/)
+ Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.

---
**Example**
```
Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]

Input: l1 = [], l2 = []
Output: []

Input: l1 = [], l2 = [0]
Output: [0]
```
---
+ 문제 1차 풀이
  1. l1혹은 l2가 비어있으면 바로 반환
  2. l1, l2를 순서대로 sort하다가 마지막에 남은 것들 다 하는 형식
```
//C#
 public class Solution {
    public ListNode MergeTwoLists(ListNode l1, ListNode l2) {
        if(l1 == null) return l2;
        if(l2 == null) return l1;

        ListNode resultNode = new ListNode();
        ListNode resultPnt = resultNode;
        ListNode l1Pnt = l1;
        ListNode l2Pnt = l2;

        

        while(l1Pnt != null && l2Pnt != null){
            if(l1Pnt.val < l2Pnt.val){
                resultPnt.val = l1Pnt.val;
                resultPnt.next = new ListNode();
                resultPnt = resultPnt.next;
                l1Pnt = l1Pnt.next;
            } 
            else{
                resultPnt.val = l2Pnt.val;
                resultPnt.next = new ListNode();
                resultPnt = resultPnt.next;
                l2Pnt = l2Pnt.next;
            }
        }
        while(l1Pnt != null){
            resultPnt.val = l1Pnt.val;
            resultPnt.next = l1Pnt.next == null ? null: new ListNode();
            resultPnt = resultPnt.next;
            l1Pnt = l1Pnt.next;
        }
        while(l2Pnt != null){
            resultPnt.val = l2Pnt.val;
            resultPnt.next = l2Pnt.next == null ? null: new ListNode();
            resultPnt = resultPnt.next;
            l2Pnt = l2Pnt.next;
        }


        return resultNode;
    }
}
```
+ Runtime: 92 ms, faster than 77.02% of C# online submissions for Merge Two Sorted Lists.
+ Memory Usage: 26.8 MB, less than 7.59% of C# online submissions for Merge Two

---
배운점
  1. 현재 문제점이 그냥 보이는 대로 코드를 짜고 문제가 생기는 부분에 대한 수정을 해서, 그런게 아닌 처음부터 구조를 명확히 잘 짜는 공부가 필요
  2. 다른 사람의 경우 어차피 반환은 2개를 합친 것이니 l1, l2 둘 중 하나에 다른 것을 next로 연결하면서 진행.
  3. 매우 효율적인 코드가 있을 것 같은데... 나중에 추가적으로 더 찾아보는 것도