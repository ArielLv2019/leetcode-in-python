- [Backtracking](#backtracking)


# Backtracking

```python
class Solution:
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        n = len(nums)
        ans = []
        def bt(start):
            if start == n:
                ans.append(nums[:])
                return

            for idx in range(start, n):
                nums[start], nums[idx] = nums[idx], nums[start]
                bt(start+1)
                nums[start], nums[idx] = nums[idx], nums[start]

        bt(0)
        return ans
```
