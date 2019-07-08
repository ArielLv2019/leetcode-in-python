- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def minSteps(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 1:
            return 0
        elif n == 2:
            return 2
        elif n % 2 == 0:
            return 2 + self.minSteps(n//2)
        else:
            for i in range(3, n, 2):
                if n % i == 0:
                    return i + self.minSteps(n//i)
            return n
```
