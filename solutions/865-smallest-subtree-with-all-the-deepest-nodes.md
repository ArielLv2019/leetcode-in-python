<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Recursion](#recursion)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Recursion

```python
class Solution(object):
    def subtreeWithAllDeepest(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        self.candidate = (root, 0)
        def height(root, dp):
            if not root: return 0
            l = height(root.left, dp + 1)
            r = height(root.right, dp + 1)

            if l == r and l + dp >= self.candidate[1]:
                self.candidate = (root, l + dp)

            return 1 + max(l,r)

        height(root, 0)
        return self.candidate[0]
```
