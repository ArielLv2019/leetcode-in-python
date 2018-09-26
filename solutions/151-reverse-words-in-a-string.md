```python
class Solution:
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        s = s[::-1]

        ans = []
        for w in s.split():
            ans.append(w[::-1])
        return ' '.join(ans)
```
