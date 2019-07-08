- [Stack](#stack)


# Stack

```python
class Solution:
    def calculate(self, s):
        """
        :type s: str
        :rtype: int
        """
        sign, n, ans = 1, len(s), 0
        stk = []
        i = 0
        while i < n:
            if s[i].isdigit():
                num = int(s[i])
                while i + 1 < n and s[i+1].isdigit():
                    num = num*10 + int(s[i+1])
                    i += 1

                ans += num * sign
            elif s[i] == '+':
                sign = 1
            elif s[i] == '-':
                sign = -1
            elif s[i] == '(':
                stk.append(ans)
                stk.append(sign)
                ans, sign = 0, 1
            elif s[i] == ')':
                # assume the input is valid
                ans = stk.pop()*ans + stk.pop()

            i += 1

        return ans
```
