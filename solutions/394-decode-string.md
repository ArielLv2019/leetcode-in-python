- [Stack](#stack)


# Stack

```python
class Solution:
    def decodeString(self, s):
        """
        :type s: str
        :rtype: str
        """
        stk = [["", 1]]
        num = ""
        for ch in s:
            if ch.isdigit():
                num += ch
            elif ch == '[':
                stk.append(["", int(num)])
                num = ""
            elif ch == ']':
                top, k = stk.pop()
                stk[-1][0] += top*k
            else:
                stk[-1][0] += ch

        return stk[0][0]
```
