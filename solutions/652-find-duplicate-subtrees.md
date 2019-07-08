- [Preorder Serialization](#preorder-serialization)


# Preorder Serialization

```python
class Solution:
    def findDuplicateSubtrees(self, root):
        """
        :type root: TreeNode
        :rtype: List[TreeNode]
        """
        from collections import defaultdict
        memo = defaultdict(list)

        def serialize(root):
            if not root: return 'null'
            s = '%s,%s,%s' % (str(root.val), serialize(root.left), serialize(root.right))
            memo[s].append(root)
            return s

        serialize(root)
        ans = []
        for s in memo:
            if len(memo[s]) > 1:
                ans.append(memo[s][0])

        return ans
```
