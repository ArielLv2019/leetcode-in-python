- [Two Stacks](#two-stacks)
- [One Stack](#one-stack)


# Two Stacks

```python
class Solution:
    def postorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        stk = [root]
        ans = []
        while stk:
            node = stk.pop()
            ans.append(node.val)

            if node.left: stk.append(node.left)
            if node.right: stk.append(node.right)

        return ans[::-1]
```

# One Stack

```python
class Solution:
    def postorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        stk = [root]
        ans = []
        while stk:
            node = stk.pop()
            ans.append(node.val)

            if node.left: stk.append(node.left)
            if node.right: stk.append(node.right)

        return ans[::-1]
```
