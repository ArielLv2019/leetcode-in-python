- [Trie + Heap](#trie--heap)


# Trie + Heap

```python
from collections import defaultdict
from heapq import heappush, heappop

class TrieNode:
    def __init__(self):
        self.children = defaultdict(TrieNode)
        self.count = 0

class AutoComplete:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word, count):
        cur = self.root
        for letter in word:
            cur = cur.children[letter]
        cur.count = count

    def startsWith(self, prefix):
        cur = self.root
        for letter in prefix:
            cur = cur.children.get(letter)
            if cur is None:
                return []

        hp = []
        def dfs(cur, path):
            if cur:
                if cur.count > 0:
                    heappush(hp, (cur.count, path))
                    if len(hp) > 3:
                        heappop(hp)

                for s, node in cur.children.items():
                        dfs(node, path+s)

        dfs(cur, prefix)
        ans = []
        while hp:
            min = heappop(hp)
            ans.append(min[1])

        return ans[::-1]
```
