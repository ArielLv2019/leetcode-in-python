<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Greedy](#greedy)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Greedy

```python
class Solution:
    def numSubarrayBoundedMax(self, A, L, R):
        """
        :type A: List[int]
        :type L: int
        :type R: int
        :rtype: int
        """
        start = count = ans = 0
        for idx in range(len(A)):
            if A[idx] > R:
                start = idx + 1
                count = 0
            elif A[idx] < L:
                ans += count
            else:
                count = idx - start + 1
                ans += count

        return ans
```

