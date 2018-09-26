<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Depth-first Search](#depth-first-search)
- [Trie](#trie)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Depth-first Search

```python
class Solution(object):
    def findWords(self, board, words):
        """
        :type board: List[List[str]]
        :type words: List[str]
        :rtype: List[str]
        """
        if not words: return []
        if not board: return []
        m = len(board)
        n = len(board[0])

        def dfs(board, word, i, j):
            if board[i][j] == word[0]:
                if not word[1:]:
                    return True
                board[i][j] = " "

                for direction in [(1, 0), (0, 1), (-1, 0), (0, -1)]:
                    new_i, new_j = i + direction[0], j + direction[1]
                    if 0 <= new_i < m and 0 <= new_j < n \
                            and dfs(board, word[1:], new_i, new_j):
                        board[i][j] = word[0]
                        return True

                board[i][j] = word[0]

            return False

        ans = set()
        for wd in words:
            for i in range(m):
                for j in range(n):
                    if dfs(board, wd, i, j):
                        ans.add(wd)

        return list(ans)
```

# Trie

```python
from collections import defaultdict

class TrieNode:
    def __init__(self):
        self.children = defaultdict(TrieNode)
        self.isWord = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        cur = self.root
        for letter in word:
            cur = cur.children[letter]
        cur.isWord = True

    def search(self, word):
        cur = self.root
        for letter in word:
            cur = cur.children.get(letter)
            if cur is None:
                return False
        return cur.isWord

    def startsWith(self, prefix):
        cur = self.root
        for letter in prefix:
            cur = cur.children.get(letter)
            if cur is None:
                return False
        return True

class Solution:
    def findWords(self, board, words):
        """
        :type board: List[List[str]]
        :type words: List[str]
        :rtype: List[str]
        """
        # construct trie
        trie = Trie()
        for w in words:
            trie.insert(w)

        ans = set()
        m, n = len(board), len(board[0])
        seen = [[False] * n for _ in range(m)]

        def dfs(i, j, prefix):            
            if not (0 <= i < m and 0 <= j < n):
                return
            
            if seen[i][j]: return

            path = prefix + board[i][j]

            if trie.search(path):
                ans.add(path)

            if trie.startsWith(path):
                if not seen[i][j]:
                    seen[i][j] = True
                    dfs(i+1, j, path)
                    dfs(i-1, j, path)
                    dfs(i, j+1, path)
                    dfs(i, j-1, path)
                    seen[i][j] = False

        for i in range(m):
            for j in range(n):
                dfs(i, j, '')

        return list(ans)
```
