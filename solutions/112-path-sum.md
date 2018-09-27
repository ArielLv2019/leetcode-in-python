<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Depth-first Search](#depth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Depth-first Search

```python
class Solution:
    def hasPathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: bool
        """
        if not root:
            return False
        
        remain = sum
        if not (root.left or root.right) and root.val == remain:
            return True
            
        remain = sum - root.val
        if self.hasPathSum(root.left, remain) or self.hasPathSum(root.right, remain):
            return True

        return False
```
