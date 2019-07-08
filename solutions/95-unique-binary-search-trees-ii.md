- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def generateTrees(self, n):
        """
        :type n: int
        :rtype: List[TreeNode]
        """

        self.memo = {}
        def construct(start, end):
            if start > end:
                return [None]
            if (start, end) not in self.memo:
                self.memo[(start, end)] = []
                for val in range(start, end + 1):
                    for left in construct(start, val - 1):
                        for right in construct(val + 1, end):
                            root = TreeNode(val)
                            root.left, root.right = left, right
                            self.memo[(start, end)].append(root)

            return self.memo[(start, end)]

        if n == 0:
            return []
        return construct(1, n)
```
