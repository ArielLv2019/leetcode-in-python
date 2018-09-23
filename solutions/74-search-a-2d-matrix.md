[TOC]

LeetCode: [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/description/)

# Binary Search

Time Complexity: O(m+n)

```python
class Solution:
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        if not matrix or target is None:
            return False

        m, n = len(matrix), len(matrix[0])

        l, r = 0, m * n - 1
        while l <= r:
            mid = (l + r) // 2
            row, col = mid // n, mid % n
            if matrix[row][col] == target:
                return True
            if matrix[row][col] < target:
                l = mid + 1
            else:
                r = mid - 1
                
        return False
```
