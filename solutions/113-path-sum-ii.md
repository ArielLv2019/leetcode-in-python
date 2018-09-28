<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Preorder Traversal](#preorder-traversal)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Preorder Traversal

```python
class Solution:
    def pathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: List[List[int]]
        """
        ans = []
        def preorder(root, path):
            if not root:
                return

            if not root.left and not root.right:
                lsum = 0
                for item in path:
                    lsum += item

                if lsum + root.val == sum:
                    ans.append(path + [root.val])

            preorder(root.left, path + [root.val])
            preorder(root.right, path + [root.val])

        preorder(root, [])
        return ans
```
