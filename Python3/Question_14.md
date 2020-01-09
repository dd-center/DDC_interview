#  Binary Tree Level Order Traversal
```python3
Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example:
Given binary tree [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
return its level order traversal as:

[
  [3],
  [9,20],
  [15,7]
]
```

🎉 Answer
```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        queue = collections.deque()
        queue.append(root)
        res = []
        while queue:
            inner_list = []
            inner_queue = collections.deque()
            while queue:
                current_node = queue.popleft()
                inner_list.append(current_node.val)
                if current_node.left:           
                    inner_queue.append(current_node.left)
                if current_node.right:
                    inner_queue.append(current_node.right)
            queue = inner_queue
            if len(inner_list) > 0:           
                res.append(inner_list)
        return res
```
