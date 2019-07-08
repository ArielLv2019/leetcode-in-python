- [Backtracking](#backtracking)
- [Bit Manipulation](#bit-manipulation)


# Backtracking

```python
class Solution:
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        ans = []

        def dfs(start, prefix):
            ans.append(prefix)
            for i in range(start, len(nums)):
                dfs(i + 1, prefix + [nums[i]])

        dfs(0, [])
        return ans
```

# Bit Manipulation

```python
class Solution:
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        ans = []
        for i in range(1<<len(nums)):
            tmp = []
            for j in range(len(nums)):
                if i & (1 << j):
                    tmp.append(nums[j])
            ans.append(tmp)
        
        return ans
```
