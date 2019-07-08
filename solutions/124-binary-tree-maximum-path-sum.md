- [Postorder Traversal](#postorder-traversal)


# Postorder Traversal

```python
class Solution(object):
    def maxPathSum(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """

        self.ans = float('-inf')

        def post(root):
            if not root:
                return 0

            lSum, rSum = post(root.left), post(root.right)
            sMax = max(root.val, root.val + max(lSum, rSum))
            self.ans = max(self.ans, sMax, root.val + lSum + rSum)
            return sMax

        post(root)
        return self.ans
```
