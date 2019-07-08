- [Two Pointers](#two-pointers)


# Two Pointers

```python
class Solution:
    def expressiveWords(self, S, words):
        """
        :type S: str
        :type words: List[str]
        :rtype: int
        """
        def check(S, W):
            i, j, m, n = 0, 0, len(S), len(W)
            for i in range(m):
                if j < n and S[i] == W[j]: 
                    j += 1
                elif S[i - 1:i + 2] != S[i] * 3 != S[i - 2:i + 1]: 
                    return False
            return j == n

        return sum(check(S, W) for W in words)
```
