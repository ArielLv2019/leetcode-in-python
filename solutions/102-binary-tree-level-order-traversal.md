<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breadth-first Search](#breadth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

LeetCode: [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)

## Breadth-first Search

Time Complexity: O(n)
Space Complexity: O(n)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        if not root:
            return []

        ans = []
        queue = [root]
        while queue:
            level = []
            nxtLevel = []

            for item in queue:
                level.append(item.val)

                if item.left:
                    nxtLevel.append(item.left)

                if item.right:
                    nxtLevel.append(item.right)

            ans.append(level)
            queue = nxtLevel

        return ans
```
