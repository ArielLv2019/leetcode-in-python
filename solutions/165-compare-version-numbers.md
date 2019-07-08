- [Queue](#queue)


# Queue

```python
class Solution:
    def compareVersion(self, version1, version2):
        v1 = version1.split(".")
        v2 = version2.split(".")
        while v1 or v2:
            val1 = int(v1.pop(0)) if v1 else 0
            val2 = int(v2.pop(0)) if v2 else 0
            if val1 > val2:
                return 1
            elif val2 > val1:
                return -1
        return 0
```
