- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def numberOfArithmeticSlices(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        if len(A) < 3: return 0
        ans, cur = 0, 0
        for i in range(1, len(A)-1):
            if A[i] - A[i-1] == A[i+1] - A[i]:
                cur += 1
                ans += cur
            else:
                cur = 0

        return ans
```
