- [Depth-first Search](#depth-first-search)



# Depth-first Search

Time Complexity: O(n)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        def dfs(l, r):
            if not l and not r: return True
            if not l: return False
            if not r: return False
            if l.val != r.val: return False

            return dfs(l.left, r.right) and dfs(l.right, r.left)
        
        if not root: return True
        return dfs(root.left, root.right)
```
