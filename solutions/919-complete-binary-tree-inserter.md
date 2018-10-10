<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breadth-first Search](#breadth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Breadth-first Search

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class CBTInserter:

    def __init__(self, root):
        """
        :type root: TreeNode
        """
        self.tree = [root]
        for node in self.tree:
            if node.left: self.tree.append(node.left)
            if node.right: self.tree.append(node.right)

    def insert(self, v):
        """
        :type v: int
        :rtype: int
        """
        n = len(self.tree)
        newNode = TreeNode(v)
        self.tree.append(newNode)
        par = self.tree[(n-1)//2]
        if n % 2 == 0:
            par.right = newNode
        else:
            par.left = newNode

        return par.val

    def get_root(self):
        """
        :rtype: TreeNode
        """
        return self.tree[0] if self.tree else None
        
# Your CBTInserter object will be instantiated and called as such:
# obj = CBTInserter(root)
# param_1 = obj.insert(v)
# param_2 = obj.get_root()
```
