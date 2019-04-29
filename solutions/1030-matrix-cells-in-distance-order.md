- [Breadth-first Search](#breadth-first-search)

# Breadth-first Search

```python
class Solution:
    def allCellsDistOrder(self, R: int, C: int, r0: int, c0: int) -> List[List[int]]:
        from collections import deque
        queue = deque([(r0, c0)])
        ans = [[r0, c0]]
        seen = {(r0, c0)}
        while queue:
            inner_queue = []
            for x, y in queue:
                for dx, dy in [(1, 0), (-1, 0), (0, 1), (0, -1)]:
                    nx, ny = x + dx, y + dy
                    if 0 <= nx < R and 0 <= ny < C and (nx, ny) not in seen:
                        seen.add((nx, ny))
                        ans.append([nx, ny])
                        inner_queue.append((nx, ny))

            queue = inner_queue

        return ans
```
