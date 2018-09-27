<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Pointers](#two-pointers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Two Pointers

```python
class Solution:
    def checkInclusion(self, s1, s2):
        """
        :type s1: str
        :type s2: str
        :rtype: bool
        """
        from collections import defaultdict
        l1, l2 = len(s1), len(s2)
        counter = defaultdict(int)
        for ch in s1:
            counter[ch] += 1

        curCounter = defaultdict(int)
        for i in range(l2 - l1 + 1):
            cur = s2[i:i+l1]
            if not curCounter:
                for ch in cur:
                    curCounter[ch] += 1
            else:
                curCounter[s2[i-1]] -= 1
                if curCounter[s2[i-1]] == 0:
                    del curCounter[s2[i-1]]
                curCounter[s2[i+l1-1]] += 1

            if counter == curCounter:
                return True

        return False
```
