- [Brute Force](#brute-force)
- [Hash Table](#hash-table)



# Brute Force

```python
class Solution:
    def isValidSudoku(self, board):
        """
        :type board: List[List[str]]
        :rtype: bool
        """
        def helper(nums):
            if not all(1 <= x <= 9 for x in nums):
                return False

            if len(set(nums)) != len(nums):
                return False

            return True

        def box(x, y):
            nums = []
            for i in range(x, x+3):
                for j in range(y, y+3):
                    if board[j][i] != '.':
                        nums.append(int(board[j][i]))

            return helper(nums)

        # check row
        for idx in range(9):
            nums = [int(x) for x in board[idx] if x != '.']
            if not helper(nums):
                return False

        # check column
        for i in range(9):
            nums = []
            for j in range(9):
                if board[j][i] != '.':
                    nums.append(int(board[j][i]))
                    
            if not helper(nums):
                return False

        # check sub-box
        for x, y in [(0,0), (3,0),(6,0),(0,3),(3,3),(6,3),(0,6),(3,6),(6,6)]:
            if not box(x, y):
                return False

        return True
```

# Hash Table

```python
class Solution:
    def isValidSudoku(self, board):
        """
        :type board: List[List[str]]
        :rtype: bool
        """
        seen = set()
        for i, row in enumerate(board):
            for j, ch in enumerate(row):
                if ch != '.':
                    for item in [(ch, i), (j, ch), (i//3, j//3, ch)]:
                        if item in seen:
                            return False
                        else:
                            seen.add(item)

        return True
```
