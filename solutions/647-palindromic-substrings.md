- [From Center to Two Sides](#from-center-to-two-sides)


# From Center to Two Sides

```python
class Solution:
    def countSubstrings(self, s):
        """
        :type s: str
        :rtype: int
        """
        ans = 0
        for idx, item in enumerate(s):
            ans += 1
            side = 1
            while idx - side >= 0 and idx + side < len(s) \
                and s[idx - side] == s[idx + side]:
                ans, side = ans + 1, side + 1

            side = 0
            while idx - side >= 0 and idx + side + 1 < len(s) \
                and s[idx - side] == s[idx + side + 1]:
                ans, side = ans + 1, side + 1

        return ans
```
