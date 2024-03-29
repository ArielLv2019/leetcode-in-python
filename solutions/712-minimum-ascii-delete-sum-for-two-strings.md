- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def minimumDeleteSum(self, s1, s2):
        """
        :type s1: str
        :type s2: str
        :rtype: int
        """
        m, n = len(s1), len(s2)
        dp = [[0] * (n+1) for _ in range(m+1)]

        for i in range(m):
            dp[i+1][0] = dp[i][0] + ord(s1[i])

        for j in range(n):
            dp[0][j+1] = dp[0][j] + ord(s2[j])

        for i in range(m):
            for j in range(n):
                if s1[i] == s2[j]:
                    dp[i+1][j+1] = dp[i][j]
                else:
                    dp[i+1][j+1] = min(dp[i][j+1]+ord(s1[i])
                                       , dp[i+1][j]+ord(s2[j]))

        return dp[-1][-1]
```
