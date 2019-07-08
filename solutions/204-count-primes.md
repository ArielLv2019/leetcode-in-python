- [Hash Table](#hash-table)


# Hash Table

```python
class Solution:
    def countPrimes(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n <= 2:
            return 0

        res = [True] * n
        res[0] = res[1] = False
        for i in range(2, n):
            if res[i]:
                for j in range(i, (n-1)//i+1, i):
                    res[i*j] = False
        return sum(res)
```
