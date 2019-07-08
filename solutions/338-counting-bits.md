- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def countBits(self, num):
        """
        :type num: int
        :ans: List[int]
        """
        ans, two = [], None
        for itr in range(num + 1):
            if (itr & itr - 1) == 0:
                if itr == 0:
                    ans.append(0)
                else:
                    ans.append(1)

                two = itr
            elif two:
                ans.append(1 + ans[itr - two])

        return ans
```
