- [Binary Search](#binary-search)



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
        if not matrix or not matrix[0]:
            return False

        m, n = len(matrix), len(matrix[0])
        row, col = 0, n - 1
        while col >= 0 and row < m:
            if target == matrix[row][col]:
                return True
            if target < matrix[row][col]:
                col -= 1
            else:
                row += 1
                
        return False
```
