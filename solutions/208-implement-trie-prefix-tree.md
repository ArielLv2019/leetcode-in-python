<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Trie](#trie)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
