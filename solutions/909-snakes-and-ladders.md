<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breadth-first Search](#breadth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Breadth-first Search

```python
class Solution:
    def snakesAndLadders(self, board):
        n = len(board)

        def get(s):
            x, y = (s-1)//n, (s-1)%n
            row = n - 1 - x
            col = y if x%2 == 0 else n - 1 - y
            return row, col

        dist = {1: 0}
        queue = [1]
        while queue:
            s = queue.pop(0)
            if s == n*n: return dist[s]
            for nxt in range(s+1, min(s+6, n*n) + 1):
                r, c = get(nxt)
                if board[r][c] != -1:
                    nxt = board[r][c]
                if nxt not in dist:
                    dist[nxt] = dist[s] + 1
                    queue.append(nxt)
        return -1
```
