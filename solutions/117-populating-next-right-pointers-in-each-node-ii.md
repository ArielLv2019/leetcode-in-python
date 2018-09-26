<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breadth-first Search with Queue](#breadth-first-search-with-queue)
- [Breadth-first Search with O(1)](#breadth-first-search-with-o1)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Breadth-first Search with Queue

```python
class Solution:
    def connect(self, root):
        if not root: return None
        queue = [root]
        while queue:
            level = []
            tail = None
            for node in queue:
                if node.left:
                    level.append(node.left)

                if node.right:
                    level.append(node.right)

                if not tail:
                    tail = node
                else:
                    tail.next = node
                    tail = tail.next

            queue = level
```

# Breadth-first Search with O(1)

```python
class Solution:
    def connect(self, root):
        dummy = child = TreeLinkNode(0)
        while root:
            while root:
                child.next = root.left
                if child.next:
                    child = child.next

                child.next = root.right
                if child.next:
                    child = child.next

                root = root.next

            root, child = dummy.next, dummy
```
