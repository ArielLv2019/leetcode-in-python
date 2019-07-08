- [Depth-first Search](#depth-first-search)
  - [Solution 1](#solution-1)
  - [Solution 2](#solution-2)


# Depth-first Search

## Solution 1

```python
class Solution:
    def connect(self, root):
        if not root or not root.left:
            return
        self.connect(root.left)
        self.connect(root.right)
        left = root.left
        right = root.right
        while left:
            left.next = right
            left = left.right
            right = right.left
```

## Solution 2

```python
class Solution:
    def helper(self, left, right):
        if not left or not right:
            return

        left.next = right
        self.helper(left.right, right.left)
        self.helper(left.left, left.right)
        self.helper(right.left, right.right)

    def connect(self, root):
        if not root:
            return

        self.helper(root.left, root.right)
```
