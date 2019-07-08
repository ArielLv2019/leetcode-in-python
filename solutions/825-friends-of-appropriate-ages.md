- [Array](#array)


# Array 

```python
class Solution:
    def numFriendRequests(self, ages):
        from collections import defaultdict
        count = defaultdict(int)
        for age in ages:
            count[age] += 1

        ans = 0
        for a, ca in count.items():
            for b, cb in count.items():
                if a * 0.5 + 7 >= b or a < b: continue
                ans += ca * cb
                if a == b: ans -= ca

        return ans
```
