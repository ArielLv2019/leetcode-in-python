- [Cheating](#cheating)
- [Dynamic Programming](#dynamic-programming)


# Cheating

```python
class Solution:
    def stoneGame(self, piles):
        """
        :type piles: List[int]
        :rtype: bool
        """
        return True
```

# Dynamic Programming

```python
class Solution:
    def stoneGame(self, p):
        n = len(p)
        # dp[i][j] means the biggest number of stones
        # that you can get more than opponent picking piles in piles[i] ~ piles[j]
        dp = [[0] * n for _ in range(n)]
        for i in range(n):
            dp[i][i] = p[i]

        for i in range(1, n):
            for j in range(i):
                dp[j][i] = max(p[j] - dp[j + 1][i], p[i] - dp[j][i - 1])

        return dp[0][-1] > 0
```
