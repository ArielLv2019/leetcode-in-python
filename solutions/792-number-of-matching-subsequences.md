- [Hash Table](#hash-table)


# Hash Table

```python
class Solution:
    def numMatchingSubseq(self, S, words):
        """
        :type S: str
        :type words: List[str]
        :rtype: int
        """
        ans = 0
        prefix = collections.defaultdict(list)
        for wd in words:
            prefix[wd[0]].append(wd)

        for s in S:
            queue = prefix[s]
            size = len(queue)
            for i in range(size):
                wd = queue.pop(0)
                if len(wd) == 1:
                    ans += 1
                else:
                    wd = wd[1:]
                    prefix[wd[0]].append(wd)

        return ans
```
