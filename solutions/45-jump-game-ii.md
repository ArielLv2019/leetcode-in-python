```python
class Solution:
    def jump(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        step = stepEdge = maxEdge = 0
        for i, n in enumerate(nums):
            if i > stepEdge:
                step += 1
                stepEdge = maxEdge

            maxEdge = max(maxEdge, i + n)
            
        return step
```
