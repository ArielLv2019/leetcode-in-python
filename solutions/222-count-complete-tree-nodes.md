<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Binary Search](#binary-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Binary Search

```python
class Solution:
    def countNodes(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        def getHeight(root):
            if not root: return 0
            return 1 + getHeight(root.left)

        if not root: return 0
        l = getHeight(root.left)
        r = getHeight(root.right)
        if l == r:
            return pow(2, l) + self.countNodes(root.right)
        else:
            return pow(2, r) + self.countNodes(root.left)
```
