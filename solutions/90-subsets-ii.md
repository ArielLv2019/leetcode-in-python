- [Backtracking](#Backtracking)

# Backtracking

```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        ans = []

        def dfs(start, prefix):
            if prefix not in ans:
                ans.append(prefix)

            for i in range(start, len(nums)):
                dfs(i + 1, prefix + [nums[i]])
                
        nums.sort()
        dfs(0, [])
        return ans
```
