- [Recursion](#recursion)


# Recursion

```python
class Solution(object):
    def subtreeWithAllDeepest(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        self.candidate = (root, 0)
        def height(root, dp):
            if not root: return 0
            l = height(root.left, dp + 1)
            r = height(root.right, dp + 1)

            if l == r and l + dp >= self.candidate[1]:
                self.candidate = (root, l + dp)

            return 1 + max(l,r)

        height(root, 0)
        return self.candidate[0]
```
