- [Trie](#trie)


# Trie

```python
from collections import defaultdict
class Node:
    def __init__(self):
        self.children = defaultdict(Node)
        self.weight = None

class Trie:
    def __init__(self):
        self.root = Node()

    def insert(self, word, weight):
        cur = self.root
        for ch in word:
            cur = cur.children[ch]

        cur.weight = weight

    def startsWith(self, prefix):
        cur = self.root
        for ch in prefix:
            if ch not in cur.children:
                return None

            cur = cur.children[ch]

        ans = set()
        queue = [cur]
        while queue:
            c = queue.pop(0)
            if c.weight is not None:
                ans.add(c.weight)

            for child in c.children.values():
                queue.append(child)

        return ans

class WordFilter(object):

    def __init__(self, words):
        """
        :type words: List[str]
        """
        self.pTree = Trie()
        self.sTree = Trie()
        self.num = len(words)
        for i, wd in enumerate(words):
            self.pTree.insert(wd, i)
            self.sTree.insert(wd[::-1], i)

    def f(self, prefix, suffix):
        """
        :type prefix: str
        :type suffix: str
        :rtype: int
        """
        ept = {i for i in range(self.num)}
        pre = self.pTree.startsWith(prefix) if prefix else ept
        post = self.sTree.startsWith(suffix[::-1]) if suffix else ept

        if pre and post:
            ans = pre & post
            if ans:
                return max(ans)

        return -1
```
