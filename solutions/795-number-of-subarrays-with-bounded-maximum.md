- [Greedy](#greedy)


# Greedy

```python
class Solution:
    def numSubarrayBoundedMax(self, A, L, R):
        """
        :type A: List[int]
        :type L: int
        :type R: int
        :rtype: int
        """
        start = count = ans = 0
        for idx in range(len(A)):
            if A[idx] > R:
                start = idx + 1
                count = 0
            elif A[idx] < L:
                ans += count
            else:
                count = idx - start + 1
                ans += count

        return ans
```

