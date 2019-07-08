- [Solution 1](#solution-1)
- [Solution 2](#solution-2)


# Solution 1

```python
class Solution:
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        def dfs(root):
            if not root: return None
            root.left, root.right = root.right, root.left
            dfs(root.left)
            dfs(root.right)

        dfs(root)
        return root
```

# Solution 2

```python
class Solution:
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        if not root: return None
        l, r = root.left, root.right
        root.left = self.invertTree(r)
        root.right = self.invertTree(l)
        return root
```
