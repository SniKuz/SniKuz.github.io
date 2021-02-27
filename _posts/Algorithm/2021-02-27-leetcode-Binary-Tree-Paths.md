---
title: "Binary Tree Paths(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/binary-tree-paths/)
+ Given a binary tree, return all root-to-leaf paths.
**Example**

```
Input:

   1
 /   \
2     3
 \
  5

Output: ["1->2->5", "1->3"]
Explanation: All root-to-leaf paths are: 1->2->5, 1->3
```

```
class Solution(object):
    def binaryTreePaths(self, root):
        """
        :type root: TreeNode
        :rtype: List[str]
        """
        if root == None: return []
        pathStr = ""
        global result
        result = []
        #
        def recursiveCheck(root, pathStr):
            pathStr += str(root.val)
            if root.left == None and root.right == None:
                result.append(pathStr)
                return 0
            pathStr += "->"
            if root.left != None: recursiveCheck(root.left, pathStr)
            if root.right != None: recursiveCheck(root.right, pathStr)
        #
        recursiveCheck(root, pathStr)
        return result
```
+ Runtime: 20 ms, faster than 69.46% of Python online submissions for Binary Tree Paths.
+ Memory Usage: 13.5 MB, less than 28.62% of Python online submissions for Binary Tree Paths.
---
