<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Sort](#sort)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Sort

```python
class Solution:
    def findMinDifference(self, timePoints):
        """
        :type timePoints: List[str]
        :rtype: int
        """
        sortedPoints = sorted(int(t[:2]) * 60 + int(t[-2:]) for t in timePoints)
        sortedPoints.append(sortedPoints[0] + 24*60)
        return min(b - a for a, b in zip(sortedPoints, sortedPoints[1:]))
```
