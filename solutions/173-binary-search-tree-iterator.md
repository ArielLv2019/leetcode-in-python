- [Stack](#stack)


# Stack

```python
class BSTIterator(object):
    def __init__(self, root):
        """
        :type root: TreeNode
        """
        self._stk = []
        cur = root
        while cur:
            self._stk.append(cur)
            cur = cur.left

    def hasNext(self):
        """
        :rtype: bool
        """
        if self._stk:
            return True

        return False

    def next(self):
        """
        :rtype: int
        """
        if self._stk:
            cur = self._stk.pop()
            ret = cur.val
            cur = cur.right
            while cur:
                self._stk.append(cur)
                cur = cur.left
                
            return ret

# Your BSTIterator will be called like this:
# i, v = BSTIterator(root), []
# while i.hasNext(): v.append(i.next())
```
