<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breadth-first Search](#breadth-first-search)
- [Depth-first Search](#depth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Breadth-first Search

```python
class Solution:
    def rightSideView(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        if not root: return []
        queue = [root]
        ans = []
        while queue:
            ans.append(queue[-1].val)
            newLayer = []
            for node in queue:
                if node.left:
                    newLayer.append(node.left)

                if node.right:
                    newLayer.append(node.right)

            queue = newLayer

        return ans
```

# Depth-first Search

```python
class Solution(object):
    def rightSideView(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        if not root: return []
        
        memo = {} # depth -> node
        def preOrder(root, depth):
            if not root: return
            if depth not in memo:
                memo[depth] = root.val

            preOrder(root.right, depth+1)
            preOrder(root.left, depth+1)

        preOrder(root, 0)
        maxDepth = max(memo.keys())
        ans = [0] * (maxDepth + 1)
        for k, v in memo.items():
            ans[k] = v

        return ans
```
