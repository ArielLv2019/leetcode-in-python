<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Hash Table](#hash-table)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Hash Table

```python
class Solution:
    def numMatchingSubseq(self, S, words):
        """
        :type S: str
        :type words: List[str]
        :rtype: int
        """
        ans = 0
        prefix = collections.defaultdict(list)
        for wd in words:
            prefix[wd[0]].append(wd)

        for s in S:
            queue = prefix[s]
            size = len(queue)
            for i in range(size):
                wd = queue.pop(0)
                if len(wd) == 1:
                    ans += 1
                else:
                    wd = wd[1:]
                    prefix[wd[0]].append(wd)

        return ans
```
