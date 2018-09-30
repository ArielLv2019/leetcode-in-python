<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Binary Search](#binary-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Binary Search

```python
import bisect, collections
class TopVotedCandidate:
    def __init__(self, persons, times):
        self.leaders = []
        count = collections.defaultdict(int)
        ld, n = None, 0

        for p, t in zip(persons, times):
            count[p] += 1
            c = count[p]
            if c >= n:
                # new leader
                if p != ld:
                    self.leaders.append((t, p))
                    ld = p

                if c > n:
                    n = c

    def q(self, t):
        i = bisect.bisect(self.leaders, (t, float('inf')), 1)
        return self.leaders[i-1][1]
```
