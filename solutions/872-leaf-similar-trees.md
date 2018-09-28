<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Preorder Traversal](#preorder-traversal)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Preorder Traversal

```python
class Solution:
    def leafSimilar(self, root1, root2):
        """
        :type root1: TreeNode
        :type root2: TreeNode
        :rtype: bool
        """
        def preOrder(root, leaves):
            if not root: return

            if not root.left and not root.right:
                leaves.append(root.val)

            preOrder(root.left, leaves)
            preOrder(root.right, leaves)

        le1, le2 = [], []
        preOrder(root1, le1)
        preOrder(root2, le2)
        return le1 == le2
```
