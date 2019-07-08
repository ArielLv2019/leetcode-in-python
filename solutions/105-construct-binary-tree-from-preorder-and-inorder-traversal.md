- [Depth-first Search](#depth-first-search)


# Depth-first Search

```python
class Solution:
    def buildTree(self, preorder, inorder):
        """
        :type inorder: List[int]
        :type postorder: List[int]
        :rtype: TreeNode
        """
        if len(inorder) == 0:
            return None
        root = TreeNode(preorder[0])
        j = inorder.index(root.val)
        root.left = self.buildTree(preorder[1:j+1], inorder[:j])
        root.right = self.buildTree(preorder[j+1:], inorder[j+1:])
        return root
```
