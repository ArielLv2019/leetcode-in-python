<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Brute Force](#brute-force)
- [KMP](#kmp)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Brute Force

```python
class Solution:
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        if not needle: return 0
        l, r = 0 , len(needle)
        while r <= len(haystack):
            if haystack[l:r] == needle:
                return l
            else:
                l += 1
                r += 1
        return -1
```

# KMP

```python
class Solution:
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        if not needle:
            return 0

        common = [0] * len(needle)
        for right in range(1, len(needle)):
            count = 0
            while count < right:
                if needle[:count+1] == needle[right-count:right+1]:
                    common[right] = count + 1
                count += 1

        next = [-1] * len(needle)
        for i in range(0, len(common)-1):
            next[i+1] = common[i]

        i = j = 0
        while i < len(haystack) and j < len(needle):
            if j == -1 or haystack[i] == needle[j]:
                i += 1
                j += 1
            else:
                j = next[j]

        return i - j if j == len(needle) else -1
```
