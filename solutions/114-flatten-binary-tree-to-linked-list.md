<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Depth-first Search](#depth-first-search)
- [Recursion](#recursion)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Depth-first Search

```python
class Solution:
    def flatten(self, root):
        """
        :type root: TreeNode
        :rtype: void Do not return anything, modify root in-place instead.
        """
        last = TreeNode(-1)
        qstack = [root]
        while qstack:
            node = qstack.pop()
            last.right = node
            last.left = None
            if node and node.right:
                qstack.append(node.right)
            if node and node.left:
                qstack.append(node.left)
            last = node
```

# Recursion

```python
class Solution:
    def flatten(self, root):
        """
        :type root: TreeNode
        :rtype: void Do not return anything, modify root in-place instead.
        """
        self.prev = None
        def post(root):
            if not root:
                return
            post(root.right)
            post(root.left)
            root.right = self.prev
            root.left = None
            self.prev = root

        post(root)
```
