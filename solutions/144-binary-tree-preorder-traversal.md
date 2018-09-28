<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Push All Nodes into Stack](#push-all-nodes-into-stack)
- [Push Right Nodes into Stack](#push-right-nodes-into-stack)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Push All Nodes into Stack

```python
class Solution:
    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        if not root: return []
        stk = [root]
        ans = []
        while stk:
            cur = stk.pop()
            ans.append(cur.val)

            if cur.right:
                stk.append(cur.right)

            if cur.left:
                stk.append(cur.left)

        return ans
```

# Push Right Nodes into Stack

```python
class Solution:
    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        stk, ans = [], []
        while root or stk:
            while root:
                ans.append(root.val)
                if root.right:
                    stk.append(root.right)

                root = root.left

            if stk:
                root = stk.pop()

        return ans
```
