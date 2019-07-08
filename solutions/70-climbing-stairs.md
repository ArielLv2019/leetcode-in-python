- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n < 3: return n

        f0, f1 = 1, 2
        for i in range(3, n+1):
            f0, f1 = f1, f0 + f1

        return f1
```
