<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breadth-first Search](#breadth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Breadth-first Search

```python
class Solution(object):
    def widthOfBinaryTree(self, root):
        if not root: return 0
        ans = 0
        queue = [(root, 0)]
        while queue:
            level = []
            if len(queue) == 1:
                ans = max(ans, 1)
            elif len(queue) > 1:
                ans = max(ans, queue[-1][1] - queue[0][1] + 1)

            for cur, idx in queue:
                if cur.left:
                    level.append((cur.left, 2*idx))

                if cur.right:
                    level.append((cur.right, 2*idx+1))

            queue = level

        return ans
```
