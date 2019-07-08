- [Stack](#stack)


# Stack

Time Complexity: O(logn)
Space Complexity: O(logn)

```python
class Solution:
    def closestKValues(self, root, target, k):
        next = []
        pre = []
        ans = []

        curr = root
        while curr:
            if target < curr.val:
                next.append(curr)
                curr = curr.left
            elif target > curr.val:
                pre.append(curr)
                curr = curr.right

        def nextLower(pre):
            l = pre.pop().left
            while l:
                pre.append(l)
                l = l.right

        def nextUpper(next):
            r = next.pop().right
            while r:
                next.append(r)
                r = r.left

        while len(ans) < k:
            if len(next) == 0 or (pre and abs(pre[-1].val - target) < abs(next[-1].val - target)):
                ans.append(pre[-1].val)
                nextLower(pre)
            else:
                ans.append(next[-1].val)
                nextUpper(next)
        return ans
```
