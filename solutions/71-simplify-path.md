- [Stack](#stack)


# Stack

```python
class Solution:
    def simplifyPath(self, path):
        """
        :type path: str
        :rtype: str
        """
        stk = []
        for dir in path.split("/"):
            if not dir or dir == '.':
                continue
            elif dir == '..':
                if stk:
                    stk.pop()
            else:
                stk.append(dir)

        return "/%s" % '/'.join(stk) if stk else "/"
```
