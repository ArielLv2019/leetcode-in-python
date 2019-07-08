- [Hash Table](#hash-table)


# Hash Table

```python
class Solution:
    def isIsomorphic(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        mapping = {}
        for idx in range(0, len(s)):
            if s[idx] in mapping and mapping[s[idx]] != t[idx]:
                return False

            if s[idx] not in mapping:
                if t[idx] in mapping.values():
                    return False

                mapping[s[idx]] = t[idx]

        return True
```
