- [Heap](#heap)


# Heap

```python
from collections import Counter
from heapq import heappop, heappush

class Solution:
    def maxSlidingWindow(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        cnt, heap, res = Counter(), [], []
        for i, num in enumerate(nums):
            heappush(heap, -num)
            cnt[num] += 1
            while not cnt[-heap[0]]:
                heappop(heap)
            if i >= k - 1:
                res.append(-heap[0])
                cnt[nums[i - k + 1]] -= 1
        return res
```
