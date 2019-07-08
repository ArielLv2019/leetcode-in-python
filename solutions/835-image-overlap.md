- [Array](#array)


# Array

```python
class Solution(object):
    def largestOverlap(self, A, B):
        N = len(A)
        count = collections.Counter()
        for i1, row1 in enumerate(A):
            for j1, v1 in enumerate(row1):
                if v1 == 1:
                    for i2, row2 in enumerate(B):
                        for j2, v2 in enumerate(row2):
                            if v2 == 1:
                                count[i1-i2, j1-j2] += 1
        return max(count.values() or [0])
```
