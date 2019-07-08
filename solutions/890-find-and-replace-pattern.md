- [Hash Table](#hash-table)


# Hash Table

```python
class Solution:
    def findAndReplacePattern(self, words, pattern):
        """
        :type words: List[str]
        :type pattern: str
        :rtype: List[str]
        """
        def match(words):
            m1 = {} # word -> pattern
            m2 = {} # pattern -> word
            for wd, p in zip(words, pattern):
                if wd in m1 and m1[wd] != p: return False
                if p in m2 and m2[p] != wd: return False

                if wd not in m1: m1[wd] = p
                if p not in m2: m2[p] = wd
            return True

        return list(filter(match, words))
```
