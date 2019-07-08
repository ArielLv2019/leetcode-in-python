- [Heap](#heap)
- [Sort](#sort)


# Heap

```python
from heapq import heappush, heappop
class Solution:
    def reorganizeString(self, S):
        hp = []
        for ch in set(S):
            heappush(hp, (-S.count(ch), ch))

        if hp and -hp[0][0] > (len(S) + 1) // 2:          
            return ''

        ans = []
        while len(hp) >= 2:
            cnt1, ch1 = heappop(hp)
            cnt2, ch2 = heappop(hp)

            if not ans or ch1 != ans[-1]:
                ans.extend([ch1, ch2])
            else:
                ans.extend([ch2, ch1])

            # count minus 1
            if cnt1 + 1: heappush(hp, (cnt1 + 1, ch1))
            if cnt2 + 1: heappush(hp, (cnt2 + 1, ch2))

        return "".join(ans) + (hp[0][1] if hp else '')
```

# Sort

```python
class Solution(object):
    def reorganizeString(self, S):
        n = len(S)
        combo = []
        for c, x in sorted([(S.count(x), x) for x in set(S)], reverse=True):
            if c > (n+1)/2: return ""
            combo.extend(c * x)
            
        ans = [None] * n
        ans[::2], ans[1::2] = combo[:(n+1)/2], combo[(n+1)/2:]
        return "".join(ans)
```


