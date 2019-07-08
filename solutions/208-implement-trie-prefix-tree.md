- [Trie](#trie)


# Trie

```python
from collections import defaultdict

class TrieNode:
    # Initialize your data structure here.
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
        


# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)
```
