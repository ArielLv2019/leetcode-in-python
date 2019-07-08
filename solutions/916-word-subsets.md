- [Hash Table](#hash-table)


# Hash Table

```python
from collections import defaultdict
class Solution(object):
    def wordSubsets(self, A, B):
        def count(word):
            counter = defaultdict(int)
            for ch in word:
                counter[ch] += 1
            return counter

        bCounter = defaultdict(int)
        for b in B:
            for ch, num in count(b).items():
                bCounter[ch] = max(bCounter[ch], num)

        ans = []
        for a in A:
            flag = True
            aCounter = count(a)
            for ch, num in bCounter.items():
                if num > aCounter[ch]:
                    flag = False
                    break

            if flag:
                ans.append(a)

        return ans
```
