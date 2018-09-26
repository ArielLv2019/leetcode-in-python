<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Stack](#stack)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
