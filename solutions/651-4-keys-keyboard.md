- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    """
    @param N: an integer
    @return: return an integer
    """

    def maxA(self, N):
        # write your code here
        dp = [i for i in range(N+1)]

        for i in range(4, N + 1):
            prev = i - 3
            count = 2
            while prev > 0:
                dp[i] = max(dp[i], dp[prev] * count)
                prev -= 1
                count += 1

        return dp[-1]
```
