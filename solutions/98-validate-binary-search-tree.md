- [Recursion](#recursion)
- [Iteration](#iteration)


# Recursion

```python
class Solution(object):
    def isValidBST(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        self.ans = True
        self.last = float('-inf')
        def inOrder(root):
            if not root: return

            inOrder(root.left)
            if root.val <= self.last:
                self.ans = False
                return
            self.last = root.val
            inOrder(root.right)

        inOrder(root)
        return self.ans
```

# Iteration

```python
class Solution(object):
    def isValidBST(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if not root: return True

        self.last = float('-inf')
        stk = []
        cur = root
        while cur or stk:
            while cur:
                stk.append(cur)
                cur = cur.left

            if stk:
                cur = stk.pop()
                if cur.val <= self.last:
                    return False
                self.last = cur.val

                cur = cur.right

        return True
```
