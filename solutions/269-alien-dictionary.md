<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Topological Sort](#topological-sort)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Topological Sort

```python
from heapq import heappop, heappush
class Solution:
    """
    @param words: a list of words
    @return: a string which is correct ans
    """
    def alienans(self, words):
        # Construct Graph
        inDegree = {ch: 0 for word in words for ch in word}
        neighbors = {ch: [] for word in words for ch in word}
        for j in range(len(words) - 1):
            for i in range(min(len(words[j]), len(words[j+1]))):
                pre, next = words[j][i], words[j+1][i]
                if pre != next:
                    inDegree[next] += 1
                    neighbors[pre].append(next)
                    break

        heap = []
        for ch, degree in inDegree.items():
            if degree == 0:
                heappush(heap, ch)
        ans = []
        while heap:
            for _ in range(len(heap)):
                ch = heappop(heap)
                ans.append(ch)
                for child in neighbors[ch]:
                    inDegree[child] -= 1
                    if inDegree[child] == 0:
                        heappush(heap, child)

        if len(ans) != len(inDegree):
            return ""
        return ''.join(ans)
```
