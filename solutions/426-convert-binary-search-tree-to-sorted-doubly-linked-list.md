- [Inorder Traversal](#inorder-traversal)


# Inorder Traversal


```python
class Solution:
    """
    @param root: The root of tree
    @return: the head of doubly list node
    """
    def bstToDoublyList(self, root):
        # write your code here
        self.last = None
        self.head = None
        def inOrder(root):
            if not root: return

            inOrder(root.left)

            if not self.head: self.head = root

            if not self.last:
                self.last = root
            else:
                self.last.right = root
                root.left = self.last
                self.last = root

            inOrder(root.right)

        inOrder(root)
        return self.head
```
