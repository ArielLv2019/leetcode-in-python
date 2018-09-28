<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Recursion](#recursion)
- [Iteration](#iteration)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Recursion

```python
class Solution(object):
    def preorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        def itr(ans, root):
            if not root:
                return

            ans.append(root.val)
            for cd in root.children:
                itr(ans, cd)

        ans = []
        itr(ans, root)
        return ans
```

# Iteration

```python
class Solution(object):
    def preorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        if not root: return []
        stk = [root]
        ans = []
        while stk:
            item = stk.pop()
            ans.append(item.val)

            for cd in item.children[::-1]:
                stk.append(cd)

        return ans
```
