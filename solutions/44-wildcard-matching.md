- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        m, n = len(s), len(p)
        dp = [[False] * (n+1) for _ in range(m+1)]
        dp[0][0] = True

        for i in range(n):
            if p[i] == '*':
                dp[0][i+1] = dp[0][i]

        for i in range(m):
            for j in range(n):
                if p[j] == '*':
                    dp[i+1][j+1] = dp[i+1][j] or dp[i][j+1]
                elif p[j] == '?' or p[j] == s[i]:
                    dp[i+1][j+1] = dp[i][j]

        return dp[-1][-1]
```
