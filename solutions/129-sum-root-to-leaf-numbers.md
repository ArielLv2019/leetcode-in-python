- [Postorder Traversal](#postorder-traversal)
- [Preorder Traversal](#preorder-traversal)


# Postorder Traversal

```python
class Solution:
    def sumNumbers(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        def dfs(root, path):
            if root:
                dfs(root.left, path * 10 + root.val)
                dfs(root.right, path * 10 + root.val)
                if not root.left and not root.right:
                    self.res += path * 10 + root.val

        self.res = 0
        dfs(root, 0)
        return self.res
```

# Preorder Traversal

```python
class Solution:
    def sumNumbers(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        self.res = 0
        def dfs(root, path):
            if not root: return
            if not root.left and not root.right:
                self.res += int(path+str(root.val))

            dfs(root.left, path+str(root.val))
            dfs(root.right, path+str(root.val))

        dfs(root, '')
        return self.res

```
