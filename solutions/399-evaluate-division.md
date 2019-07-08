- [Depth-first Search](#depth-first-search)


# Depth-first Search

```python
class Solution:
    def calcEquation(self, equations, values, queries):
        """
        :type equations: List[List[str]]
        :type values: List[float]
        :type queries: List[List[str]]
        :rtype: List[float]
        """
        from collections import defaultdict
        neighbors = defaultdict(list)
        graph = {}
        for i in range(len(values)):
            v = values[i]
            x, y = equations[i]
            graph[(x, y)] = v
            neighbors[x].append(y)
            neighbors[y].append(x)

        ans = []

        def dfs(sx, sy):
            if sx not in neighbors:
                ans.append(-1)
                return
            
            stk = [(sx, 1)]
            visited = {sx}
            while stk:
                cur, val = stk.pop()
                if cur == sy:
                    ans.append(val)
                    return

                for nxt in neighbors[cur]:
                    if nxt not in visited:
                        visited.add(nxt)

                        if (cur, nxt) in graph:
                            v = graph[(cur, nxt)]
                        else:
                            v = 1 / graph[(nxt, cur)]

                        stk.append((nxt, val * v))

            ans.append(-1)

        for ix, iy in queries:
            dfs(ix, iy)

        return ans
```
