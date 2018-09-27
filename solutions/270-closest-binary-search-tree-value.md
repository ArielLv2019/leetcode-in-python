<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Binary Search](#binary-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Binary Search

```python
class Solution:
    def __init__(self):
        self.ans = float('inf')

    def closestValue(self, root, target):
        # write your code here
        if root is None:
            return self.ans

        if root.val == target:
            return root.val

        if abs(root.val - target) < abs(self.ans - target):
            self.ans = root.val

        if target > root.val:
            right = self.closestValue(root.right, target)
            if abs(right - target) < abs(self.ans - target):
                return right
        else:
            left = self.closestValue(root.left, target)
            if abs(left - target) < abs(self.ans - target):
                return left
            
        return self.ans
```
