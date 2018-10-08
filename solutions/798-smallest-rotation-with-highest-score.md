<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Array](#array)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Array

```python
class Solution:
    def bestRotation(self, A):
        n = len(A)
        lostScore = [1] * n
        for i in range(n):
            lostScore[(i - A[i] + 1) % n] -= 1

        leftSum, maxItem, ans = 0, float('-inf'), 0
        for i in range(0, n):
            lostScore[i] += leftSum
            leftSum = lostScore[i]
            if lostScore[i] >= maxItem:
                maxItem = lostScore[i]
                ans = i

        return ans
```
