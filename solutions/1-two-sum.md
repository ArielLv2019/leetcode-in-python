- [Brute Force](#brute-force)
- [Sort and Two Pointers](#sort-and-two-pointers)
- [Two-pass Hash Table](#two-pass-hash-table)
- [One-pass Hash Table](#one-pass-hash-table)


# Brute Force

Time Complexity: O(n^2)

```python
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        for idx, item in enumerate(nums):
            for newIdx, newItem in enumerate(nums[idx+1:]):
                if (item + newItem == target):
                    return [idx, idx+1+newIdx]
```

# Sort and Two Pointers

Time Complexity: O(nlogn)
Space Complexity: O(n)

```python
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        tuples = [(item, idx) for idx, item in enumerate(nums)]
        sortNum = sorted(tuples, key=lambda x:x[0])

        start, end = 0, len(nums) - 1
        while start <= end:
            if sortNum[start][0] + sortNum[end][0] > target:
                end -= 1
            elif sortNum[start][0] + sortNum[end][0] < target:
                start += 1
            else:
                return [sortNum[start][1], sortNum[end][1]]

        return []
```

# Two-pass Hash Table

Time Complexity: O(n)
Space Complexity: O(n)

```python
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        mem = {n: i for i, n in enumerate(nums)}

        for i, n in enumerate(nums):
            if (target - n) in mem and mem[target-n] != i:
                return [i, mem[target-n]]

        return None
```

Trick Points:

- Consider some edge cases, such [3, 3], 6. The index of answers should be different.

# One-pass Hash Table

Following the last solution, two-pass is not necessary, because when you visit the current item, you just need to query the elements before it.

```python
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        mem = {}
        for i, n in enumerate(nums):
            if (target - n) in mem:
                return [mem[target-n], i]
            mem[n] = i

        return None
```
