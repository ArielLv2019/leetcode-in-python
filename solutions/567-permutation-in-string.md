- [Two Pointers](#two-pointers)


# Two Pointers

```python
class Solution:
    def checkInclusion(self, s1, s2):
        """
        :type s1: str
        :type s2: str
        :rtype: bool
        """
        from collections import defaultdict
        l1, l2 = len(s1), len(s2)
        counter = defaultdict(int)
        for ch in s1:
            counter[ch] += 1

        curCounter = defaultdict(int)
        for i in range(l2 - l1 + 1):
            cur = s2[i:i+l1]
            if not curCounter:
                for ch in cur:
                    curCounter[ch] += 1
            else:
                curCounter[s2[i-1]] -= 1
                if curCounter[s2[i-1]] == 0:
                    del curCounter[s2[i-1]]
                curCounter[s2[i+l1-1]] += 1

            if counter == curCounter:
                return True

        return False
```
