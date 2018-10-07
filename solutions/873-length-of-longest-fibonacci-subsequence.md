<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Dynamic Programming](#dynamic-programming)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Dynamic Programming

```python
class Solution:
    def lenLongestFibSubseq(self, A):
        n = len(A)
        index = {x: i for i, x in enumerate(A)}
        dp = [[2] *  n for _ in range(n)]

        ans = 0
        for i in range(n):
            for j in range(i):
                k = index.get(A[i]- A[j], None)
                if k and k < j:
                    dp[j][i] = dp[k][j] + 1
                    ans = max(ans, dp[j][i])

        return ans if ans >= 3 else 0
```