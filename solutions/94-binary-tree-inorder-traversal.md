- [Stack](#stack)


# Stack

```python
class Solution:
    def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        stack, ans = [], []
        while root or stack:
            while root:
                stack.append(root)
                root = root.left

            if stack:
                root = stack.pop()
                ans.append(root.val)
                root = root.right

        return ans
```
