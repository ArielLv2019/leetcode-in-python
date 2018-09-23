<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Depth-first Search](#depth-first-search)
  - [Breadth-first Search](#breadth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

LeetCode: [Remove Invalid Parentheses](https://leetcode.com/problems/remove-invalid-parentheses/description/)

# Depth-first Search

```python
class Solution:
    def removeInvalidParentheses(self, s):
        """
        :type s: str
        :rtype: List[str]
        """
        lp = rp = 0
        for ch in s:
            if ch == '(':
                lp += 1
            elif ch == ')':
                if lp > 0:
                    lp -= 1
                else:
                    rp += 1

        # lp means the number of left parentheses that need to remove
        # rp means the number of right parentheses that need to remove
        res = set()
        def dfs(i, lp, rp, prefix, opens):
            if i == len(s) and lp == 0 and rp == 0 and opens == 0:
                res.add(prefix)
                return

            if lp < 0 or rp < 0 or opens < 0 or i == len(s):
                return

            if s[i] == '(':
                dfs(i+1, lp, rp, prefix+s[i], opens+1) # use this '('
                dfs(i+1, lp-1, rp, prefix, opens) # NOT use
            elif s[i] == ')':
                dfs(i+1, lp, rp, prefix+s[i], opens-1) # use this ')'
                dfs(i+1, lp, rp-1, prefix, opens) # NOT use
            else:
                dfs(i+1, lp, rp, prefix+s[i], opens)

        dfs(0, lp, rp, '', 0)
        return list(res)
```

## Breadth-first Search

```python
class Solution(object):
    def removeInvalidParentheses(self, s):
        """
        :type s: str
        :rtype: List[str]
        """
        lp = rp = 0
        for ch in s:
            if ch == '(':
                lp += 1
            elif ch == ')':
                if lp > 0:
                    lp -= 1
                else:
                    rp += 1

        queue, visited = [(s, lp, rp)], set()
        ans = []
        while queue:
            cand, lp, rp = queue.pop(0)
            
            if lp == rp == 0 and self.isValid(cand):
                ans.append(cand)
            else:
                for i in range(len(cand)):
                    if cand[i] == '(' or cand[i] == ')':
                        nxtCand = cand[:i] + cand[i+1:]
                        if nxtCand not in visited:
                            visited.add(nxtCand)

                            if cand[i] == '(' and lp > 0:
                                queue.append((nxtCand, lp-1, rp))
                            elif cand[i] == ')' and rp > 0:
                                queue.append((nxtCand, lp, rp-1))

        return ans

    def isValid(self, s):
        cnt = 0
        for c in s:
            if c == '(':
                cnt += 1
            if c == ')':
                cnt -= 1
            if cnt < 0:
                return False
        return cnt == 0
```
