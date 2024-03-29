- [One-pass traversal](#one-pass-traversal)


# One-pass traversal

Time Complexity: O(m+n)
Space Complexity: O(1)

```python
class Solution:
    def countBattleships(self, board):
        """
        :type board: List[List[str]]
        :rtype: int
        """
        if not board: return 0
        m, n = len(board), len(board[0])

        count = 0
        for i in range(m):
            for j in range(n):
                if board[i][j] == '.':
                    continue
                if i > 0 and board[i-1][j] == 'X':
                    continue
                if j > 0 and board[i][j-1] == 'X':
                    continue

                count += 1

        return count
```
