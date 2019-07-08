- [Binary Search](#binary-search)


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
