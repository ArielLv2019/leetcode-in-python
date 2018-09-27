<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Postorder Traversal](#postorder-traversal)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
