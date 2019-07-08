- [Recursion](#recursion)


# Recursion

```python
class Solution:
    def lowestCommonAncestor(self, root, p, q):
        """
        :type root: TreeNode
        :type p: TreeNode
        :type q: TreeNode
        :rtype: TreeNode
        """
        if p.val > q.val: p, q = q, p
        def post(root, p, q):
            if not root: return None
            if root.val > q.val:
                return post(root.left, p, q)
            
            if root.val < p.val:
                return post(root.right, p, q)
                
            return root
        
        return post(root, p, q) 
```
