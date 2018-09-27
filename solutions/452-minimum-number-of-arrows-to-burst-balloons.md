<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Sort](#sort)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Sort

```python
class Solution:
    def findMinArrowShots(self, points):
        """
        :type points: List[List[int]]
        :rtype: int
        """
        if not points: return 0
        points.sort(key=lambda x:x[1])
        ans = 0
        tail = float('-inf')
        for start, end in points:
            if start > tail:
                ans, tail = ans + 1, end

        return ans
```
