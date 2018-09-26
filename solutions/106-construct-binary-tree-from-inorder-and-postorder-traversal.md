<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Recursion](#recursion)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Recursion

```python
class Solution:
    def buildTree(self, inorder, postorder):
        """
        :type inorder: List[int]
        :type postorder: List[int]
        :rtype: TreeNode
        """
        if len(inorder) == 0: return None
        root = TreeNode(postorder[-1])
        j = inorder.index(postorder[-1])
        root.left = self.buildTree(inorder[:j],postorder[:j])
        root.right = self.buildTree(inorder[j+1:],postorder[j:-1])
        return root
```
