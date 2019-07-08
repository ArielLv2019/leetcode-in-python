- [Depth-first Search](#depth-first-search)


# Depth-first Search

```python
class Solution:
    """
    @param m: an integer
    @param n: an integer
    @return: the total number of unlock patterns of the Android lock screen
    """
    def numberOfPatterns(self, m, n):
        # Write your code here
        self.visited = [[False] * 3 for _ in range(3)]
        self.ans = 0

        def canJump(x1, y1, x2, y2):
            if self.visited[x2][y2]: return False
            dx, dy = abs(x1-x2), abs(y1-y2)

            # adjacent
            if dx <= 1 and dy <= 1: return True

            # horizontal
            if dx == 0 and dy == 2: return self.visited[x1][1]

            # vertical
            if dy == 0 and dx == 2: return self.visited[1][y1]

            # di
            if dx == dy == 2: return self.visited[1][1]

            return True

        def dfs(sx, sy, c):
            if m <= c <= n: 
                self.ans += 1
            
            if c >= n:
                return
            
            self.visited[sx][sy] = True
            for i in range(3):
                for j in range(3):
                    if canJump(sx, sy, i, j):
                        dfs(i, j, c+1)
                        
            self.visited[sx][sy] = False

        dfs(0,0,1)
        dfs(0,1,1)

        self.ans *= 4

        dfs(1,1,1)
```
