---
title: "LeetCode -Add Two Nums(Mid)"
excerpt: "Add Two Numbers"
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/add-two-numbers/)
+ You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

+ You may assume the two numbers do not contain any leading zero, except the number 0 itself.

---
**Example 1:**
```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```
---
+ 문제 1차 풀이
  1. l1, l2의 총 길이를 while문으로 구한 뒤 더하는 방식으로 진행 -> Nullref
  2. 초기 어떤 오류인지 next가 null로만 떠서 재실행 _OK
  3. 코드가 너무 난잡한 것 같아 솔루션을 참고, 좋은 코드라 생각.
```
//C#
public class Solution {
    public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
			ListNode curL1 = l1;
			ListNode curL2 = l2;
			ListNode result = new ListNode();
			ListNode curList = result;
			int sum = 0;
			while(curL1 != null || curL2 != null){
				sum = sum /10;
				if(curL1 != null){
					sum += curL1.val;
					curL1 = curL1.next;
				}
				if(curL2 != null){
					sum += curL2.val;
					curL2 = curL2.next;
				}
				curList.next = new ListNode(sum % 10);
				curList = curList.next;
			}
			if(sum / 10 == 1) curList.next = new ListNode(1);
			return result.next;
    }
}
```
+ Runtime: 108 ms, faster than 66.27% of C# online submissions for Two Sum.
+ Memory Usage: 28.5 MB, less than 22.33% of C# online submissions for Two Sum.

---
배운점
  1. 처음에 오류인지 ListNode.next에서 Null이 계속 뜨는거에서 코드에 확신이 없었다.
  2. 첫 시도의 경우 코드가 깔끔하지 않고 읽기 힘들었다 생각하는데 노력이 필요.
  3. 후하 Stay calm