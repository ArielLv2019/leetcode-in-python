<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Stacks](#two-stacks)
- [One Stack](#one-stack)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Two Stacks

```python
class Solution:
    def postorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        stk = [root]
        ans = []
        while stk:
            node = stk.pop()
            ans.append(node.val)

            if node.left: stk.append(node.left)
            if node.right: stk.append(node.right)

        return ans[::-1]
```

# One Stack

```python
class Solution:
    def postorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        stk = [root]
        ans = []
        while stk:
            node = stk.pop()
            ans.append(node.val)

            if node.left: stk.append(node.left)
            if node.right: stk.append(node.right)

        return ans[::-1]
```
