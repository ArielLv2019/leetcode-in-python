<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Backtracking](#backtracking)
- [Iteration](#iteration)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Backtracking

```python
class Solution:
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        if not digits: return []
        n = len(digits)
        mapping = ["abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"]
        ans = []
        def dfs(start, path):
            if start == n:
                ans.append(path)
                return

            for ch in mapping[int(digits[start]) - 2]:
                dfs(start+1, path + ch)

        dfs(0, "")
        return ans
```

# Iteration

```python
class Solution:
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        chars = ["abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"]
        ans = []
        for d in digits:
            if 2 <= int(d) <= 9:
                if not ans:
                    for ch in chars[int(d)-2]:
                        ans.append(ch)
                else:
                    tmp = []
                    for idx in range(len(ans)):
                        for ch in chars[int(d)-2]:
                            tmp.append(ans[idx] + ch)
                    ans = tmp

        return ans
```
