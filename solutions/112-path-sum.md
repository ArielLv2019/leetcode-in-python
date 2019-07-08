- [Depth-first Search](#depth-first-search)


# Depth-first Search

```python
class Solution:
    def hasPathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: bool
        """
        if not root:
            return False
        
        remain = sum
        if not (root.left or root.right) and root.val == remain:
            return True
            
        remain = sum - root.val
        if self.hasPathSum(root.left, remain) or self.hasPathSum(root.right, remain):
            return True

        return False
```
