```py
class Solution:
    def generateTrees(self, n: int) -> list[TreeNode | None]:
        if n == 0:
            return []
        def dfs(start, end):
            if start>end:
                return [None]
            
            all_trees = []
            for i in range(start, end+1):
                left = dfs(start, i-1)
                right = dfs(i+1, end)

                for l in left:
                    for r in right:
                        curr = TreeNode(i)
                        curr.left = l
                        curr.right = r
                        all_trees.append(curr)
            return all_trees
        return dfs(1,n)
```

<img width="860" height="646" alt="image" src="https://github.com/user-attachments/assets/eb4a4ae5-1252-46aa-a5c6-ccc5096041e0" />
