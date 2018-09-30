<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Traversals](#two-traversals)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Two Traversals

```python
class Solution:
    def partitionDisjoint(self, A):
        n = len(A)
        maxLeft = [A[0]] * n
        minRight = [A[-1]] * n

        for i in range(1, n):
            maxLeft[i] = max(maxLeft[i-1], A[i-1])

        for i in range(n-2, -1, -1):
            minRight[i] = min(minRight[i+1], A[i+1])

        for i in range(0, n):
            if maxLeft[i] <= minRight[i]:
                return i+1
```
