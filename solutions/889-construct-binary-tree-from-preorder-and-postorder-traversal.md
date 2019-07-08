- [Recursion](#recursion)


# Recursion

```python
class Solution:
    def constructFromPrePost(self, pre, post):
        """
        :type pre: List[int]
        :type post: List[int]
        :rtype: TreeNode
        """
        if not pre: return None
        root = TreeNode(pre[0])
        if len(post) >= 2:
            rIdx = pre.index(post[-2])
            root.left = self.constructFromPrePost(pre[1:rIdx], post[:rIdx-1])
            root.right = self.constructFromPrePost(pre[rIdx:], post[rIdx-1:-1])
        return root
```
