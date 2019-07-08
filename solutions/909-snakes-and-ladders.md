- [Breadth-first Search](#breadth-first-search)


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
