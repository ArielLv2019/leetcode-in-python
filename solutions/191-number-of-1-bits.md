- [Math](#math)


# Math

```python
class Solution(object):
    def hammingWeight(self, n):
        """
        :type n: int
        :rtype: int
        """
        ans = 0
        while n > 0:
            if n & 1 == 1:
                ans += 1

            n >>= 1

        return ans
```

With syntactic sugar

```python
class Solution(object):
    def hammingWeight(self, n):
        """
        :type n: int
        :rtype: int
        """
        ans = 0
        while n:
            if n & 1:
                ans += 1

            n >>= 1

        return ans
```
