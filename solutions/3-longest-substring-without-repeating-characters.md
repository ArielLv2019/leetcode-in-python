<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [One-pass Hash Table with Two Pointers](#one-pass-hash-table-with-two-pointers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
