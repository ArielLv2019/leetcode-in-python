- [Breadth-first Search](#Breadth-first-Search)

# Breadth-first Search

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isCousins(self, root: TreeNode, x: int, y: int) -> bool:
        queue = [(root, None)] 
        while queue:
            inner_queue = []
            count = 0
            x_parent = y_parent = None
            for cur, parent in queue:
                if cur.val == x:
                    count += 1
                    x_parent = parent
                elif cur.val == y:
                    count += 1
                    y_parent = parent

                if cur.left: inner_queue.append((cur.left, cur))
                if cur.right: inner_queue.append((cur.right, cur))
            
            if count == 2:
                if x_parent and y_parent and x_parent != y_parent:
                    return True
                else:
                    return False

            if count == 1: return False
            queue = inner_queue

        return False
```
