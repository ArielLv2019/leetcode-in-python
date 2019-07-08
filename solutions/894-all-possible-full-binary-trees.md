- [Recursion](#recursion)


# Recursion

```python
class Solution:
    def allPossibleFBT(self, N):
        self.memo = {}

        def construct(n):
            if n == 0: return []
            if n == 1: return [TreeNode(0)]

            if n not in self.memo:
                ans = []
                for i in range(1,n,2):
                    for left in construct(i):
                        for right in construct(n - i - 1):
                            root = TreeNode(0)
                            root.left = left
                            root.right = right
                            ans.append(root)

                self.memo[N] = ans

            return self.memo[N]

        return construct(N)
```
