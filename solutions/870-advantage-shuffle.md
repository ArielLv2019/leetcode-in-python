- [Greedy](#greedy)


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
