- [Math](#math)


# Math

```python
class Solution:
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        ans = 0
        for ch in s:
            ans = ans * 26 + ord(ch) - ord('A') + 1

        return ans
```
