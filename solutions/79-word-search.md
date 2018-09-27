<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Depth-first Search](#depth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Depth-first Search

```python
class Solution:
    def exist(self, board, word):
        """
        :type board: List[List[str]]
        :type word: str
        :rtype: bool
        """
        if not word: return True
        if not board: return False
        m = len(board)
        n = len(board[0])

        def dfs(board, word, i, j):
            if board[i][j] == word[0]:
                if not word[1:]:
                    return True

                for direction in [(1,0), (0,1), (-1,0),(0,-1)]:
                    board[i][j] = " "
                    new_i, new_j = i + direction[0], j + direction[1]
                    if 0 <= new_i < m and 0 <= new_j < n \
                        and dfs(board, word[1:], new_i, new_j):
                        return True
                    board[i][j] = word[0]


            return False

        for i in range(m):
            for j in range(n):
                if dfs(board, word, i, j):
                    return True

        return False
```
