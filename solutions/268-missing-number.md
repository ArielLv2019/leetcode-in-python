- [Sum](#sum)
- [XOR](#xor)


# Sum

```python
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        return n * (n+1)/2 - sum(nums) if n > 0 else 0
```

# XOR

```python
class Solution:
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ans = len(nums)
        for i in range(len(nums)):
            ans ^= i
            ans ^= nums[i]

        return ans
```
