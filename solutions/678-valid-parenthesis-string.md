- [Recursion](#recursion)
- [Two Stacks](#two-stacks)
- [Greedy](#greedy)


# Recursion

```python
class Solution(object):
    def checkValidString(self, s):
        def bt(start, openings):
            if openings < 0: return False

            for idx in range(start, len(s)):
                if s[idx] == '(':
                    openings += 1
                elif s[idx] == ')':
                    if openings <= 0: return False
                    openings -= 1
                elif s[idx] == '*':
                    return bt(idx+1, openings) or bt(idx+1, openings-1) \
                        or bt(idx+1, openings+1)

            return openings == 0

        return bt(0, 0)
```

# Two Stacks

```python
class Solution:
    def checkValidString(self, s):
        left, star = [], []
        for i, ch in enumerate(s):
            if ch == '(':
                left.append(i)
            elif ch == '*':
                star.append(i)
            elif ch == ')':
                if not left and not star: return False
                if left:
                    left.pop()
                else:
                    star.pop()

        while left and star:
            if left.pop() > star.pop():
                return False

        return len(left) == 0

```

# Greedy

```python
class Solution(object):
    def checkValidString(self, s):
        leftMin = leftMax = 0
        for ch in s:
            leftMin = leftMin + 1 if ch == '(' else max(leftMin - 1, 0)
            leftMax = leftMax - 1 if ch == ')' else leftMax + 1
            if leftMax < 0: return False
        return leftMin == 0
```
