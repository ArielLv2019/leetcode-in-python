<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Math](#math)
- [Breadth-first Search](#breadth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Math

```python
class Solution:
    def canMeasureWater(self, x, y, z):
        """
        :type x: int
        :type y: int
        :type z: int
        :rtype: bool
        """
        if x + y < z: return False
        if x == z or y == z or x + y == z: return True

        return z % self.gcd(x, y) == 0

    def gcd(self, x, y):
        if y == 0: return x

        x, y = y, x % y
        return self.gcd(x, y)
```

# Breadth-first Search

```python
class Solution:
    def canMeasureWater(self, x, y, z):
        """
        :type x: int
        :type y: int
        :type z: int
        :rtype: bool
        """
        if x > y:
            x, y = y, x

        if x + y < z: return False
        queue = [(0, 0)]
        visited = {(0, 0)}

        while queue:
            a, b = queue.pop(0)
            if a + b == z:
                return True

            neighbors = set()
            neighbors.add((x,b))
            neighbors.add((a,y))
            neighbors.add((0,b))
            neighbors.add((a,0))
            # pour y to x
            if a + b < x:
                neighbors.add((min(x, b+a), 0))
            else:
                neighbors.add((min(x, b+a), b-(x-a)))

            # pour x to y
            if a + b < y:
                neighbors.add((0, min(b+a, y)))
            else:
                neighbors.add((a-(y-b), min(b+a, y)))

            for nxt in neighbors:
                if nxt not in visited:
                    visited.add(nxt)
                    queue.append(nxt)

        return False
```
