- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def numMusicPlaylists(self, N, L, K):
        dp = [[0] * (N+1) for _ in range(L+1)]
        dp[0][0] = 1

        # State transition: the last song is played for first time or not
        for i in range(L):
            for j in range(N):
                dp[i+1][j+1] = dp[i][j]*(N-j+1) + dp[i][j+1]*max(j-K, 0)

        return dp[-1][-1] % (10**9+7)
```
