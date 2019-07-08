- [Depth-first Search](#depth-first-search)
- [Recursion: Postorder](#recursion-postorder)
- [Recursion: Preorder](#recursion-preorder)


# Depth-first Search

```python
class Solution:
    def flatten(self, root):
        """
        :type root: TreeNode
        :rtype: void Do not return anything, modify root in-place instead.
        """
        last = TreeNode(-1)
        qstack = [root]
        while qstack:
            node = qstack.pop()
            last.right = node
            last.left = None
            if node and node.right:
                qstack.append(node.right)
            if node and node.left:
                qstack.append(node.left)
            last = node
```

# Recursion: Postorder

```python
class Solution:
    def flatten(self, root):
        """
        :type root: TreeNode
        :rtype: void Do not return anything, modify root in-place instead.
        """
        self.prev = None
        def post(root):
            if not root:
                return
            post(root.right)
            post(root.left)
            root.right = self.prev
            root.left = None
            self.prev = root

        post(root)
```

# Recursion: Preorder

```python
class Solution:
    def flatten(self, root):
        """
        :type root: TreeNode
        :rtype: void Do not return anything, modify root in-place instead.
        """
        self.prev = TreeNode(0)
        def preOrder(root):
            if not root: return

            l = root.left
            r = root.right

            self.prev.right = root
            root.left = None
            self.prev = root

            preOrder(l)
            preOrder(r)

        preOrder(root)
```
