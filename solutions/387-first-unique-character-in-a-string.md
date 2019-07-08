- [Counter](#counter)
- [Recording Index](#recording-index)


# Counter

```python
class Solution:
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        from collections import defaultdict
        counter = defaultdict(int)
        for ch in s:
            counter[ch] += 1

        for idx, ch in enumerate(s):
            if counter[ch] == 1:
                return idx
            
        return -1
```

# Recording Index

```python
class Solution:
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        rIndex = {}
        for idx, ch in enumerate(s):
            rIndex[ch] = idx

        mores = set()
        for idx, ch in enumerate(s):
            if idx < rIndex[ch]:
                mores.add(ch)
            elif idx == rIndex[ch] and ch not in mores:
                return idx

        return -1
```
