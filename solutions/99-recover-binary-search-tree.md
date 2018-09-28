<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Inorder Traversal](#inorder-traversal)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Inorder Traversal

```python
class Solution:
    def recoverTree(self, root):
        """
        :type root: TreeNode
        :rtype: void Do not return anything, modify root in-place instead.
        """
        self.last = TreeNode(float('-inf'))
        self.first = self.second = None

        def inOrder(root):
            if not root: return
            inOrder(root.left)

            if not self.first and self.last.val >= root.val:
                self.first = self.last

            if self.first and self.last.val >= root.val:
                self.second = root

            self.last = root

            inOrder(root.right)

        inOrder(root)
        if self.first and self.second:
            self.first.val, self.second.val = self.second.val, self.first.val
```
