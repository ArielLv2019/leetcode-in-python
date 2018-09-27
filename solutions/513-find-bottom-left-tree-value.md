<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breadth-first Search](#breadth-first-search)
- [Depth-first Search](#depth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Breadth-first Search

Level order traversal

```python
class Solution:
    def findBottomLeftValue(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if not root: return None
        queue = [root]
        ans = []
        while queue:
            ans = queue[0].val

            level = []
            for node in queue:
                if node.left:
                    level.append(node.left)

                if node.right:
                    level.append(node.right)

            queue = level

        return ans

```
# Depth-first Search

Preorder traversal

```python
class Solution:
    def findBottomLeftValue(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        self.candidate = (-1, None)
        def preOrder(root, depth):
            if not root: return

            if depth > self.candidate[0]:
                self.candidate = (depth, root.val)

            preOrder(root.left, depth+1)
            preOrder(root.right, depth+1)

        preOrder(root, 0)
        return self.candidate[1]
```
