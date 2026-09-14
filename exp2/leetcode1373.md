```py
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxSumBST(self, root: Optional[TreeNode]) -> int:
        self.ans = 0
        def dfs(node):
            if not node:
                return True, float('inf'), float('-inf'), 0

            lbst, lmin, lmax, lsum = dfs(node.left)
            rbst, rmin, rmax, rsum = dfs(node.right)

            if lbst and rbst and lmax<node.val<rmin:
                total = lsum + node.val +rsum
                self.ans = max(self.ans, total)
                
                return True, min(lmin, node.val), max(rmax, node.val), total
            
            return False, float('-inf'), float('inf'), 0
        
        dfs(root)
        return self.ans
```

<img width="757" height="522" alt="image" src="https://github.com/user-attachments/assets/b2b0725c-1ebc-4683-9ad4-46ff572fa3bb" />
