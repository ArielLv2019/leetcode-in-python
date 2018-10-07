<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Depth-first Search](#depth-first-search)
- [Topological Sort](#topological-sort)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Depth-first Search

```python
class Solution:
    def canFinish(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype: bool
        """
        graph = [[] for _ in range(numCourses)]
        visit = [0 for _ in range(numCourses)]
        for x, y in prerequisites:
            graph[x].append(y)

        def dfs(i):
            if visit[i] == -1:
                return False
            if visit[i] == 1:
                return True
            visit[i] = -1
            for j in graph[i]:
                if not dfs(j):
                    return False
            visit[i] = 1
            return True

        for i in range(numCourses):
            if not dfs(i):
                return False
        return True
```

# Topological Sort

```python
class Solution:
    def canFinish(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype: bool
        """
        inDegree = {i: 0 for i in range(numCourses)}
        neighbors = {i: [] for i in range(numCourses)}

        for pre, nxt in prerequisites:
            inDegree[nxt] += 1
            neighbors[pre].append(nxt)

        from heapq import heappush, heappop
        hp = []
        for k, v in inDegree.item():
            if v == 0:
                heappush(hp, k)

        ans = []
        while hp:
            cur = heappop(hp)
            ans.append(cur)
            for nxt in neighbors[cur]:
                inDegree[nxt] -= 1
                if inDegree[nxt] == 0:
                    heappush(hp, nxt)

        return ans if len(ans) == numCourses else []
```
