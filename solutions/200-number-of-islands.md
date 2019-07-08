- [Depth-first Search](#depth-first-search)
- [Breadth-first Search](#breadth-first-search)


# Depth-first Search

```python
class Solution:
    def numIslands(self, grid):
        """
        :type grid: List[List[str]]
        :rtype: int
        """
        if not grid or not grid[0]: return 0

        m, n = len(grid), len(grid[0])

        def dfs(grid, r, c):
            grid[r][c] = '0'
            directions = [(0, 1), (1, 0), (0, -1), (-1, 0)]
            for dir in directions:
                new_r, new_c = r + dir[0], c + dir[1]
                if 0 <= new_r < m and 0 <= new_c < n and grid[new_r][new_c] == '1':
                    dfs(grid, new_r, new_c)


        count = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1':
                    dfs(grid, i, j)
                    count += 1

        return count
```

# Breadth-first Search


```python
class Solution:
    def numIslands(self, grid):
        """
        :type grid: List[List[str]]
        :rtype: int
        """
        if not grid or not grid[0]: return 0

        m, n = len(grid), len(grid[0])

        def bfs(grid, r, c):
            queue = [(r, c)]
            grid[r][c] = '0'
            while queue:
                i, j = queue.pop()
                directions = [(0,1), (1,0), (0,-1), (-1,0)]
                for dir in directions:
                    new_i, new_j = i + dir[0], j + dir[1]
                    if 0 <= new_i < m and 0 <= new_j < n and grid[new_i][new_j] == '1':
                        queue.append((new_i, new_j))
                        grid[new_i][new_j] = '0'

        count = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1':
                    bfs(grid, i, j)
                    count += 1

        return count
```
