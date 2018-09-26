```python
class Solution:
    def setZeroes(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: void Do not return anything, modify matrix in-place instead.
        """
        rowFlag = False
        colFlag = False
        for i in range(len(matrix)):
            for j in range(len(matrix[i])):
                if i == 0 and matrix[i][j] == 0:
                    rowFlag = True

                if j == 0 and matrix[i][j] == 0:
                    colFlag = True

                if matrix[i][j] == 0:
                    matrix[0][j] = 0
                    matrix[i][0] = 0

        for i in range(1, len(matrix)):
            for j in range(1, len(matrix[i])):
                if matrix[0][j] == 0 or matrix[i][0] == 0:
                    matrix[i][j] = 0
                    
        if rowFlag:
            for i in range(len(matrix[0])):
                matrix[0][i] = 0

        if colFlag:
            for i in range(len(matrix)):
                matrix[i][0] = 0
```
