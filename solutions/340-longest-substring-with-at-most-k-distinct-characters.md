<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Hash Table & Two Pointers](#hash-table--two-pointers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Hash Table & Two Pointers

```python
class Solution:
    def lengthOfLongestSubstringKDistinct(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        from collections import defaultdict
        longest, start, distinct, visited = 0, 0, 0, defaultdict(int)
        for i, ch in enumerate(s):
            if visited[ch] == 0:
                distinct += 1
            visited[ch] += 1

            while distinct > k:
                visited[s[start]] -= 1
                if visited[s[start]] == 0:
                    distinct -= 1
                start += 1

            # distinct <= k
            longest = max(longest, i - start + 1)
        return longest
```
