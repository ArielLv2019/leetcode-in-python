- [Recursion](#recursion)


# Recursion

```python
class Solution:
    def buildTree(self, inorder, postorder):
        """
        :type inorder: List[int]
        :type postorder: List[int]
        :rtype: TreeNode
        """
        if len(inorder) == 0: return None
        root = TreeNode(postorder[-1])
        j = inorder.index(postorder[-1])
        root.left = self.buildTree(inorder[:j],postorder[:j])
        root.right = self.buildTree(inorder[j+1:],postorder[j:-1])
        return root
```
