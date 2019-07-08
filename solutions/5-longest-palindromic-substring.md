- [From Middle to Two Ends](#from-middle-to-two-ends)



# From Middle to Two Ends

```python
class Solution:
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        # odd
        res = s[0]
        for idx, item in enumerate(s):
            cur_max = 1
            left, mid, right = idx - 1, idx, idx + 1
            while left >= 0 and right < len(s) and \
                    s[left] == s[right]:
                cur_max += 2
                if cur_max >= len(res):
                    res = s[left:right+1]

                left -= 1
                right += 1

        # even
        for idx, item in enumerate(s):
            cur_max = 0
            left, right = idx, idx + 1
            while left >= 0 and right < len(s) and \
                    s[left] == s[right]:
                cur_max += 2
                if cur_max >= len(res):
                    res = s[left:right + 1]

                left -= 1
                right += 1

        return res
```
