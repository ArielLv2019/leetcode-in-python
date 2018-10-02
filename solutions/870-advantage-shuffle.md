<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Greedy](#greedy)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Greedy

```python
class Solution(object):
    def advantageCount(self, A, B):
        sortedA = sorted(A)
        sortedB = sorted(B)

        bigger = {b: [] for b in B} # list for duplicates
        lost = []

        i = 0
        for a in sortedA:
            if a > sortedB[i]:
                bigger[sortedB[i]].append(a)
                i += 1
            else:
                lost.append(a)

        ans = []
        for b in B:
            nxt = bigger[b].pop() if bigger[b] else lost.pop()
            ans.append(nxt)

        return ans
```
