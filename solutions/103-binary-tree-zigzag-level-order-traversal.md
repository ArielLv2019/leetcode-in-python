- [Breadth-first Search](#breadth-first-search)


# Breadth-first Search

```python
class Solution(object):
    def zigzagLevelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        if not root:
            return []

        ans, queue = [], [root]
        flag = 1
        while queue:
            if flag > 0:
                ans.append([node.val for node in queue])
            else:
                ans.append([node.val for node in queue[::-1]])

            flag = -flag

            level = []
            for node in queue:
                if node.left:
                    level.append(node.left)
                if node.right:
                    level.append(node.right)
            queue = level
        return ans
```
