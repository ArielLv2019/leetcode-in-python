- [Preorder Traversal](#preorder-traversal)


# Preorder Traversal

```python
class Solution:
    def pathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: List[List[int]]
        """
        ans = []
        def preorder(root, path):
            if not root:
                return

            if not root.left and not root.right:
                lsum = 0
                for item in path:
                    lsum += item

                if lsum + root.val == sum:
                    ans.append(path + [root.val])

            preorder(root.left, path + [root.val])
            preorder(root.right, path + [root.val])

        preorder(root, [])
        return ans
```
