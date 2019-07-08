- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def lenLongestFibSubseq(self, A):
        n = len(A)
        index = {x: i for i, x in enumerate(A)}
        dp = [[2] *  n for _ in range(n)]

        ans = 0
        for i in range(n-1):
            for j in range(i):
                k = index.get(A[j] + A[i], None)
                if k and k > i:
                    dp[i][k] = dp[j][i] + 1
                    ans = max(ans, dp[i][k])

        return ans if ans >= 3 else 0
```
