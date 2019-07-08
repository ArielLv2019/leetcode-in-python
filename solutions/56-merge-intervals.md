- [Sort](#sort)


# Sort

```python
class Solution:
    def merge(self, intervals):
        """
        :type intervals: List[Interval]
        :rtype: List[Interval]
        """
        ans = []
        for i in sorted(intervals, key=lambda i: i.start):
            if ans and i.start <= ans[-1].end:
                ans[-1].end = max(ans[-1].end, i.end)
            else:
                ans += i
        return ans
```
