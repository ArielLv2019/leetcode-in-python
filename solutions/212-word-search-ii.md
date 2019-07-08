- [Depth-first Search](#depth-first-search)
- [Trie](#trie)
- [Depth-fist Search with One Less Recursion](#depth-fist-search-with-one-less-recursion)


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
class TrieNode():
    def __init__(self):
        self.children = collections.defaultdict(TrieNode)
        self.isWord = False

class Trie():
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for w in word:
            node = node.children[w]
        node.isWord = True

class Solution:
    def findWords(self, board, words):
        trie = Trie()
        for w in words:
            trie.insert(w)

        m, n = len(board), len(board[0])
        ans = []
        seen = [[False] * n for _ in range(m)]
        def dfs(board, node, i, j, path):
            if node.isWord:
                ans.append(path)
                node.isWord = False

            if i < 0 or i >= m or j < 0 or j >= n:
                return

            cur = board[i][j]
            node = node.children.get(cur)
            if not node:
                return

            for di, dj in [(1, 0), (0, 1), (-1, 0), (0, -1)]:
                if not seen[i][j]:
                    ni, nj = i + di, j + dj
                    seen[i][j] = True
                    dfs(board, node, ni, nj, path+cur)
                    seen[i][j] = False

        node = trie.root
        for i in range(m):
            for j in range(n):
                dfs(board, node, i, j, "")
        return ans
```

# Depth-fist Search with One Less Recursion

```python
class TrieNode():
    def __init__(self):
        self.children = collections.defaultdict(TrieNode)
        self.isWord = False

class Trie():
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for w in word:
            node = node.children[w]
        node.isWord = True

class Solution:
    def findWords(self, board, words):
        trie = Trie()
        for w in words:
            trie.insert(w)

        m, n = len(board), len(board[0])
        ans = []
        seen = [[False] * n for _ in range(m)]
        def dfs(board, node, i, j, path):            
            cur = board[i][j]
            node = node.children.get(cur)
            if not node:
                return
            elif node.isWord:
                ans.append(path+cur)
                node.isWord = False

            for di, dj in [(1, 0), (0, 1), (-1, 0), (0, -1)]:
                ni, nj = i + di, j + dj
                if 0 <= ni < m and 0 <= nj < n and not seen[ni][nj]:
                    seen[i][j] = True
                    dfs(board, node, ni, nj, path+cur)
                    seen[i][j] = False

        node = trie.root
        for i in range(m):
            for j in range(n):
                dfs(board, node, i, j, "")
        return ans
```
