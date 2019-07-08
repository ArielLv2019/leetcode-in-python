- [Preorder Traversal](#preorder-traversal)


# Preorder Traversal

```python
class Solution:
    def leafSimilar(self, root1, root2):
        """
        :type root1: TreeNode
        :type root2: TreeNode
        :rtype: bool
        """
        def preOrder(root, leaves):
            if not root: return

            if not root.left and not root.right:
                leaves.append(root.val)

            preOrder(root.left, leaves)
            preOrder(root.right, leaves)

        le1, le2 = [], []
        preOrder(root1, le1)
        preOrder(root2, le2)
        return le1 == le2
```
