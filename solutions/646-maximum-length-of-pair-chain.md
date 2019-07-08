- [Greedy](#greedy)
- [Dynamic Programming](#dynamic-programming)


# Greedy

```python
class Solution:
    def findLongestChain(self, pairs):
        """
        :type pairs: List[List[int]]
        :rtype: int
        """
        cur, res = float('-inf'), 0
        for p in sorted(pairs, key=lambda x: x[1]):
            if cur < p[0]:
                cur, res = p[1], res + 1
        return res
```

# Dynamic Programming

```python
class Solution:
    def findLongestChain(self, pairs):
        """
        :type pairs: List[List[int]]
        :rtype: int
        """
        pairs.sort(key=lambda x: x[0])
        n = len(pairs)
        dp = [1] * n
        for i in range(n):
            for j in range(i):
                if pairs[i][0] > pairs[j][1]:
                    dp[i] = max(dp[i], dp[j]+1)

        return dp[-1]
```
