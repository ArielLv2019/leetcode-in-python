<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Breadth-first Search](#breadth-first-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Breadth-first Search

```python
class Codec:

    def serialize(self, root):
        """Encodes a tree to a single string.

        :type root: TreeNode
        :rtype: str
        """
        if not root: return ""
        ans = []
        queue = [root]
        while queue:
            cur = queue.pop(0)
            if cur:
                queue.append(cur.left)
                queue.append(cur.right)
                ans.append(str(cur.val))
            else:
                ans.append('#')

        return ','.join(ans)

    def deserialize(self, data):
        """Decodes your encoded data to tree.

        :type data: str
        :rtype: TreeNode
        """
        if not data: return None
        nodes = data.split(',')
        root = TreeNode(int(nodes[0]))
        queue = [root]
        index = 1
        while queue:
            node = queue.pop(0)
            if nodes[index] != '#':
                node.left = TreeNode(int(nodes[index]))
                queue.append(node.left)
            index += 1

            if nodes[index] != '#':
                node.right = TreeNode(int(nodes[index]))
                queue.append(node.right)
                
            index += 1
        return root
        

# Your Codec object will be instantiated and called as such:
# codec = Codec()
# codec.deserialize(codec.serialize(root))
```
