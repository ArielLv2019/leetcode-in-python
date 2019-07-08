
```python
import random
class Solution:

    def __init__(self, nums):
        self.nums = nums

    def reset(self):
        return self.nums

    def shuffle(self):
        ans = self.nums[:]
        n = len(ans)
        for i in range(n):
            j = random.randint(i, n-1)
            ans[i], ans[j] = ans[j], ans[i]
        return ans
        


# Your Solution object will be instantiated and called as such:
# obj = Solution(nums)
# param_1 = obj.reset()
# param_2 = obj.shuffle()
```
