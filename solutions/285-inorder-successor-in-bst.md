```python
class Solution:
    """
    @param: root: The root of the BST.
    @param: p: You need find the successor node of p.
    @return: Successor of p.
    """
    def inorderSuccessor(self, root, p):
        # write your code here
        candidate = None
        while root:
            if p.val < root.val:
                candidate = root
                root = root.left
            else:
                root = root.right

        return candidate
```
