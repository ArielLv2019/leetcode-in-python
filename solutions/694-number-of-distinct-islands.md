- [Breadth-first Search](#breadth-first-search)


# Breadth-first Search

```python
class Solution:
    def numberofDistinctIslands(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        if not grid:
            return 0

        m, n = len(grid), len(grid[0])
        islands, ans = set(), 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1:
                    path = ''
                    queue = [(i, j)]
                    grid[i][j] = 0
                    while queue:
                        x, y = queue.pop(0)
                        for dx, dy in [(1,0),(0,1),(-1,0),(0,-1)]:
                            nx, ny = x+dx, y+dy
                            if 0 <= nx < m and 0 <= ny < n and grid[nx][ny] == 1:
                                queue.append((nx, ny))
                                grid[nx][ny] = 0
                                path += str(nx-i) + str(ny-j)

                    if path not in islands:
                        ans += 1
                        islands.add(path)
        return ans
```
