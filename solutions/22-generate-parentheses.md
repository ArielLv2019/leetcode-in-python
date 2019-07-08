- [Backtracking](#backtracking)


# Backtracking

```python
class Solution:
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        ans = []
        def bt(left, right, prefix):
            if right < left: return
            if left == right == 0:
                ans.append(prefix)

            if left > 0:
                bt(left-1, right, prefix+'(')

            if right > 0:
                bt(left, right-1, prefix+')')

        bt(n, n, '')
        return ans
```
