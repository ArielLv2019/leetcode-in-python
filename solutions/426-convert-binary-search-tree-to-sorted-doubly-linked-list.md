<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Inorder Traversal](#inorder-traversal)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Inorder Traversal


```python
class Solution:
    """
    @param root: The root of tree
    @return: the head of doubly list node
    """
    def bstToDoublyList(self, root):
        # write your code here
        self.last = None
        self.head = None
        def inOrder(root):
            if not root: return

            inOrder(root.left)

            if not self.head: self.head = root

            if not self.last:
                self.last = root
            else:
                self.last.right = root
                root.left = self.last
                self.last = root

            inOrder(root.right)

        inOrder(root)
        return self.head
```
