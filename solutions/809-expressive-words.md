<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Pointers](#two-pointers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Two Pointers

```python
class Solution:
    def expressiveWords(self, S, words):
        """
        :type S: str
        :type words: List[str]
        :rtype: int
        """
        def check(S, W):
            i, j, m, n = 0, 0, len(S), len(W)
            for i in range(m):
                if j < n and S[i] == W[j]: 
                    j += 1
                elif S[i - 1:i + 2] != S[i] * 3 != S[i - 2:i + 1]: 
                    return False
            return j == n

        return sum(check(S, W) for W in words)
```
