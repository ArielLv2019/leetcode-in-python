- [Breadth-first Search](#breadth-first-search)
- [Depth-first Search](#depth-first-search)


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
