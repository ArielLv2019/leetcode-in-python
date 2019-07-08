- [Recursion](#recursion)
- [Iteration](#iteration)


# Recursion

```python
class Solution(object):
    def preorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        def itr(ans, root):
            if not root:
                return

            ans.append(root.val)
            for cd in root.children:
                itr(ans, cd)

        ans = []
        itr(ans, root)
        return ans
```

# Iteration

```python
class Solution(object):
    def preorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        if not root: return []
        stk = [root]
        ans = []
        while stk:
            item = stk.pop()
            ans.append(item.val)

            for cd in item.children[::-1]:
                stk.append(cd)

        return ans
```
