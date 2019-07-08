- [Stack](#stack)


# Stack

```python
class Solution:
    def calculate(self, s):
        ans = 0
        num, n = 0, len(s)
        sign = '+'
        stack = []

        for i in range(n):
            ch = s[i]

            if ch.isdigit():
                num = 10 * num + int(ch)

            if ch != ' ' and not ch.isdigit() or i + 1 == n:
                if sign == '+':
                    stack.append(num)
                elif sign == '-':
                    stack.append(-num)
                elif sign == '*':
                    last = stack.pop()
                    stack.append(last * num)
                elif sign == '/':
                    last = stack.pop()
                    stack.append(int(last / num))

                sign = ch
                num = 0

        for num in stack:
            ans += num

        return ans

```
