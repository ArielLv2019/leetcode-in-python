- [Stack](#stack)

# Stack

Time Complexity: O(n)
Space Complexity: O(n)

```python
class Solution:
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stk = []
        for item in s:
            if item == '(' or item == '[' or item == '{':
                stk.append(item)
            elif item == ')':
                if not stk or stk[-1] != '(':
                    return False
                else:
                    stk.pop()
            elif item == ']':
                if not stk or stk[-1] != '[':
                    return False
                else:
                    stk.pop()
            elif item == '}':
                if not stk or stk[-1] != '{':
                    return False
                else:
                    stk.pop()

        if stk:
            return False

        return True
```

Using dictionary makes it simplier.

```python
class Solution:
    def isValid(self, s: str) -> bool:
        pairs = {
            '}': '{',
            ')': '(',
            ']': '[',
        }

        stk = []
        for char in s:
            if char in pairs.values():
                stk.append(char)
            elif char in pairs.keys():
                if not stk or stk[-1] != pairs[char]:
                    return False
                else:
                    stk.pop()

        return True if not stk else False
```
