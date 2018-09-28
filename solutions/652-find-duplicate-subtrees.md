<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Preorder Serialization](#preorder-serialization)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Preorder Serialization

```python
class Solution:
    def findDuplicateSubtrees(self, root):
        """
        :type root: TreeNode
        :rtype: List[TreeNode]
        """
        from collections import defaultdict
        memo = defaultdict(list)

        def serialize(root):
            if not root: return 'null'
            s = '%s,%s,%s' % (str(root.val), serialize(root.left), serialize(root.right))
            memo[s].append(root)
            return s

        serialize(root)
        ans = []
        for s in memo:
            if len(memo[s]) > 1:
                ans.append(memo[s][0])

        return ans
```
