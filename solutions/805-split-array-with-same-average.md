```python
class Solution(object):
    def splitArraySameAverage(self, A):
        """
        :type A: List[int]
        :rtype: bool
        """
        A.sort()
        target = float(sum(A)) / len(A)
        used = set()
        def dfs(start, cnt, total):
            if (cnt, total) in used: return False
            if cnt:
                avg = float(total)/cnt
                if avg == target:
                    return True
                elif avg > target:
                    used.add((cnt, total))
                    return False
            for i in range(start+1, len(A)):
                if dfs(i, cnt+1, total+A[i]): 
                    return True
            used.add((cnt, total))
            return False
        return dfs(0, 0, 0)
```
