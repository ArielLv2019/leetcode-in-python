- [String](#string)


# String

```python
class Solution:
    def removeComments(self, source):
        inBlock = False
        ans, newLine = [], []
        for line in source:
            idx = 0
            if not inBlock:
                newLine = []

            while idx < len(line):
                if line[idx:idx+2] == '/*' and not inBlock:
                    inBlock = True
                    idx += 1
                elif line[idx:idx+2] == '*/' and inBlock:
                    inBlock = False
                    idx += 1
                elif line[idx:idx+2] == '//' and not inBlock :
                    break
                elif not inBlock:
                    newLine.append(line[idx])

                # step forward even the above conditions are all false
                # which means in block
                idx += 1

            if newLine and not inBlock:
                ans.append(''.join(newLine))

        return ans
```
