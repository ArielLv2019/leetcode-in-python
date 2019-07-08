- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def subarrayBitwiseORs(self, A):
        ans, cur = set(), set()
        for item in A:
            cur = {item | prev for prev in cur} | {item}
            ans |= cur
        return len(ans)
```
