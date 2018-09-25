<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [One-pass Traversal](#one-pass-traversal)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# One-pass Traversal

```python
class Solution:
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        if not strs: return ''
        minLen = min(map(len, strs))
        idx, ans = 0, ''
        flag = True
        while idx < minLen:
            cur = strs[-1][idx]
            for st in strs[:-1]:
                if st[idx] != cur:
                    flag = False
                    break
                    
            if flag:
                ans += cur
                idx += 1
            else:
                break

        return ans
```
