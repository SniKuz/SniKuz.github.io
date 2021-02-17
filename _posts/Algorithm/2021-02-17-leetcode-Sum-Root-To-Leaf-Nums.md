---
title: "Sum Root to Leaf Numbers(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/unique-paths/)
+ Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number.
+ An example is the root-to-leaf path 1->2->3 which represents the number 123.
+ Find the total sum of all root-to-leaf numbers.
+ Note: A leaf is a node with no children.
---
**Example**

```
Input: [4,9,0,5,1]
    4
   / \
  9   0
 / \
5   1
Output: 1026
Explanation:
The root-to-leaf path 4->9->5 represents the number 495.
The root-to-leaf path 4->9->1 represents the number 491.
The root-to-leaf path 4->0 represents the number 40.
Therefore, sum = 495 + 491 + 40 = 1026.
```

+ 문제 1차 풀이
  1. 재귀로 진행, 뭔가 잘 안진행되서 사전에 일일이 넣는 방식으로 진행(넣고, 오른쪽 가지가 있으면 추가하고 등)
  2. 재귀 방식 더 고민 및 다른 사람의 풀이 방식 참고


```
//C#
 public class Solution {
    public int SumNumbers(TreeNode root, int no=0) {
        if(root==null) return 0;
        no = no*10 + root.val;
        if(root.left==null && root.right==null) return no;
        return SumNumbers(root.left,no)+SumNumbers(root.right,no);
    }
}
```
+ Runtime: 92 ms, faster than 69.65% of C# online submissions for Sum Root to Leaf Numbers.
+ Memory Usage: 25.1 MB, less than 23.88% of C# online submissions for Sum Root to Leaf Numbers.

+ 고민
  1. 유니티를 주로 써본거지 C#, C++, Java, 파이썬 등 제대로 잘 알고 있는 언어가 없다. 필요할 때 찾아보며 한 정도... 2개정도 선택해서 집중 공부가 필요하다 생각한다.