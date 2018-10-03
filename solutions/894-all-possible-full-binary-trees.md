<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Recursion](#recursion)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
