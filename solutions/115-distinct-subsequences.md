- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def numDistinct(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: int
        """
        m, n = len(s), len(t)
        dp = [[0] * (n+1) for _ in range(m+1)]

        for i in range(m+1):
            dp[i][0] = 1

        for i in range(m):
            for j in range(n):
                if s[i] == t[j]:
                    dp[i+1][j+1] = dp[i][j] + dp[i][j+1]
                else:
                    dp[i+1][j+1] = dp[i][j+1]

        return dp[-1][-1]
```
