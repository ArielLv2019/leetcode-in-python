```python
class Solution:
    def countNodes(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        def getHeight(root):
            if not root: return 0
            return 1 + getHeight(root.left)

        if not root: return 0
        l = getHeight(root.left)
        r = getHeight(root.right)
        if l == r:
            return pow(2, l) + self.countNodes(root.right)
        else:
            return pow(2, r) + self.countNodes(root.left)
```
