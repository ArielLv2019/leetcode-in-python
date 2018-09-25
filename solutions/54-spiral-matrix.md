<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Matrix Transposition](#matrix-transposition)
- [Layer-by-Layer](#layer-by-layer)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Matrix Transposition

```python
class Solution:
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        m = len(matrix)
        if m == 1:
            return matrix[0]

        res = []
        while len(matrix) > 0:
            res += matrix[0]
            matrix.pop(0)
            matrix = list(map(list, zip(*matrix)))
            matrix.reverse()

        return res
```

# Layer-by-Layer

```python
class Solution:
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        ans = []
        def cycle(x1, y1, x2, y2):
            for x in range(x1, x2+1):
                ans.append(matrix[y1][x])

            for y in range(y1+1, y2+1):
                ans.append(matrix[y][x2])

            if y1 != y2:
                for x in range(x2-1, x1-1, -1):
                    ans.append(matrix[y2][x])

            if x1 != x2:
                for y in range(y2-1, y1, -1):
                    ans.append(matrix[y][x1])

            if x1 + 1 <= x2 - 1 and y1 + 1 <= y2 - 1:
                cycle(x1+1, y1+1, x2-1, y2-1)

        if matrix:
            m, n = len(matrix), len(matrix[0])
            cycle(0, 0, n-1, m-1)
        return ans
```
