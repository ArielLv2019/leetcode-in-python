<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Depth-first Search](#depth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Depth-first Search

```python
class Solution:
    def buildTree(self, preorder, inorder):
        """
        :type inorder: List[int]
        :type postorder: List[int]
        :rtype: TreeNode
        """
        if len(inorder) == 0:
            return None
        root = TreeNode(preorder[0])
        j = inorder.index(root.val)
        root.left = self.buildTree(preorder[1:j+1], inorder[:j])
        root.right = self.buildTree(preorder[j+1:], inorder[j+1:])
        return root
```
