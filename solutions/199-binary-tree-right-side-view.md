- [Breadth-first Search](#breadth-first-search)
- [Depth-first Search](#depth-first-search)


# Breadth-first Search

```python
class Solution:
    def rightSideView(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        if not root: return []
        queue = [root]
        ans = []
        while queue:
            ans.append(queue[-1].val)
            newLayer = []
            for node in queue:
                if node.left:
                    newLayer.append(node.left)

                if node.right:
                    newLayer.append(node.right)

            queue = newLayer

        return ans
```

# Depth-first Search

```python
class Solution(object):
    def rightSideView(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        if not root: return []
        
        memo = {} # depth -> node
        def preOrder(root, depth):
            if not root: return
            if depth not in memo:
                memo[depth] = root.val

            preOrder(root.right, depth+1)
            preOrder(root.left, depth+1)

        preOrder(root, 0)
        maxDepth = max(memo.keys())
        ans = [0] * (maxDepth + 1)
        for k, v in memo.items():
            ans[k] = v

        return ans
```
