<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Stack](#stack)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Stack

Time Complexity: O(logn)
Space Complexity: O(logn)

```python
class Solution:
    def closestKValues(self, root, target, k):
        next = []
        pre = []
        res = []

        curr = root
        while curr:
            if target < curr.val:
                next.append(curr)
                curr = curr.left
            elif target > curr.val:
                pre.append(curr)
                curr = curr.right

        def nextLower(pre):
            l = pre.pop().left
            while l:
                pre.append(l)
                l = l.right

        def nextUpper(next):
            r = next.pop().right
            while r:
                next.append(r)
                r = r.left

        while len(res) < k:
            if len(next) == 0 or (pre and abs(pre[-1].val - target) < abs(next[-1].val - target)):
                res.append(pre[-1].val)
                nextLower(pre)
            else:
                res.append(next[-1].val)
                nextUpper(next)
        return res
```
