<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Hash Table](#hash-table)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
