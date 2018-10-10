<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Dynamic Programing with Two-pass](#dynamic-programing-with-two-pass)
- [Dynamic Programming with One-pass](#dynamic-programming-with-one-pass)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Dynamic Programing with Two-pass

```python
class Solution(object):
    def maxSubarraySumCircular(self, A):
        # ans1: answer for one-interval subarray
        ans1 = cur = float('-inf')
        for x in A:
            cur = max(cur + x, x)
            ans1 = max(ans1, cur)

        # ans2: answer for two-interval subarray
        ans2 = cur = float('inf')
        for i in range(1, len(A)-1):
            cur = min(A[i] + cur, A[i])
            ans2 = min(ans2, cur)
        ans2 = sum(A) - ans2

        return max(ans1, ans2)
```

# Dynamic Programming with One-pass

```python
class Solution(object):
    def maxSubarraySumCircular(self, A):
        total = 0
        maxSum = curMax = -float('inf')
        minSum = curMin = float('inf')
        for a in A:
            total += a
            curMax = max(curMax + a, a)
            maxSum = max(maxSum, curMax)
            curMin = min(curMin + a, a)
            minSum = min(minSum, curMin)

        return max(maxSum, total - minSum) if maxSum > 0 else maxSum
```
