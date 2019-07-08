- [Stack](#stack)


# Stack

```python
class Solution:
    def sumSubarrayMins(self, A):
        MOD = 10**9 + 7

        stk = []
        ans = prod = 0
        for x in A:
            count = 1
            while stk and stk[-1][0] >= x:
                y, c = stk.pop()
                prod -= y * c
                count += c

            stk.append((x, count))
            prod += x * count
            ans += prod

        return ans % MOD
```
