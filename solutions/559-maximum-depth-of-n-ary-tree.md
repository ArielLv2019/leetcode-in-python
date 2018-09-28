<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breadth-first Search](#breadth-first-search)
- [Depth-first Search](#depth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Breadth-first Search

```python
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: Node
        :rtype: int
        """
        if not root:
            return 0

        count = 0
        qe = [root]
        while qe:
            level = []
            while qe:
                item = qe.pop(0)
                for cdr in item.children:
                    level.append(cdr)

            count += 1
            qe = level

        return count
```

# Depth-first Search

```python
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: Node
        :rtype: int
        """
        def dfs(root):
            if not root: return 0
            if not root.children: return 1

            ans = 0
            for cd in root.children:
                ans = max(ans, dfs(cd)+1)

            return ans

        return dfs(root)
```
