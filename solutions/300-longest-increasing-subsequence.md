- [Dynamic Programming](#dynamic-programming)
  - [Binary Search](#binary-search)


# Dynamic Programming

```python
class Solution:
    def lengthOfLIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums: return 0
        N = len(nums)
        # lengths[i] = longest ending in nums[i]
        lengths = [1] * N

        for i in range(len(nums)):
            for j in range(i):
                if nums[j] < nums[i]:
                    if lengths[j] >= lengths[i]:
                        lengths[i] = lengths[j] + 1

        return max(lengths)
```

## Binary Search

```python
class Solution:
    def lengthOfLIS(self, nums):
        tails = [0] * len(nums)
        ans = 0
        for x in nums:
            i, j = 0, ans
            while i < j:
                m = (i + j) // 2
                if tails[m] < x:
                    i = m + 1
                else:
                    j = m
            tails[i] = x
            ans = max(i + 1, ans)
        return ans
```
