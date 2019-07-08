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
        dp = [[False] * (m+1) for _ in range(n+1)]
        dp[0][0] = True

        for i in range(n):
            if p[i] == '*':
                dp[i+1][0] = dp[i-1][0]

        for i in range(n):
            for j in range(m):
                if p[i] == '*':
                    dp[i+1][j+1] |= dp[i-1][j+1]  # a* counts as empty
                    if p[i-1] in {s[j], '.'}: # a* counts single/multiple a
                        dp[i+1][j+1] |= dp[i+1][j] or dp[i][j+1]
                elif p[i] in {s[j], '.'}:
                    dp[i+1][j+1] = dp[i][j]

        return dp[-1][-1]

```
