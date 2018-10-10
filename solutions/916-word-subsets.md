<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Hash Table](#hash-table)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Hash Table

```python
from collections import defaultdict
class Solution(object):
    def wordSubsets(self, A, B):
        def count(word):
            counter = defaultdict(int)
            for ch in word:
                counter[ch] += 1
            return counter

        bCounter = defaultdict(int)
        for b in B:
            for ch, num in count(b).items():
                bCounter[ch] = max(bCounter[ch], num)

        ans = []
        for a in A:
            flag = True
            aCounter = count(a)
            for ch, num in bCounter.items():
                if num > aCounter[ch]:
                    flag = False
                    break

            if flag:
                ans.append(a)

        return ans
```
