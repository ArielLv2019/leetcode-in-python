<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Hash Table](#hash-table)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
