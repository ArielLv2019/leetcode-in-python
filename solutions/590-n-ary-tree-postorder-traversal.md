- [Recursion](#recursion)
- [Iteration](#iteration)


# Recursion

```python
class Solution(object):
    def postorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        def iter(ans, root):
            if not root:
                return

            for cd in root.children:
                iter(ans, cd)

            ans.append(root.val)

        ans = []
        iter(ans, root)
        return ans
```

# Iteration

```python
class Solution(object):
    def postorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        if not root: return []
        stk = [root]
        ans = []
        while stk:
            root = stk.pop()
            ans.append(root.val)
            for cd in root.children:
                stk.append(cd)

        return ans[::-1]

```
