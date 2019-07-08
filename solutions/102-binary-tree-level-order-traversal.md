- [Breadth-first Search](#breadth-first-search)



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
