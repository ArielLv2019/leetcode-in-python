- [Binary Search](#binary-search)


# Binary Search

Time Complexity: O(logn)

```python
class Solution:
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        if not nums:
            return -1

        low, high = 0, len(nums) - 1

        while low <= high:
            mid = (low + high) // 2
            if target == nums[mid]:
                return mid

            # left side is sorted
            # low and mid can be the same index
            if nums[low] <= nums[mid]: 
                if nums[low] <= target <= nums[mid]:
                    high = mid - 1
                else:
                    low = mid + 1
            else: # right side is sorted
                if nums[mid] <= target <= nums[high]:
                    low = mid + 1
                else:
                    high = mid - 1

        return -1

```
