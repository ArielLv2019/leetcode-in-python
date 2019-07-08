- [One-pass Hash Table with Two Pointers](#one-pass-hash-table-with-two-pointers)


# One-pass Hash Table with Two Pointers

```python
class Solution:
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        used = {}
        ans = start = 0
        for i, c in enumerate(s):
            if c in used and start <= used[c]:
                start = used[c] + 1
            else:
                ans = max(ans, i - start + 1)

            used[c] = i

        return ans
```
