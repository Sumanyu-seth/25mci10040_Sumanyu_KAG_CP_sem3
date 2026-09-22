```py
class Solution:
    def findOrder(self, numCourses: int, prerequisites: list[list[int]]) -> list[int]:
        deg = {u:0 for u in range(numCourses)}
        neigh = [[] for i in range(numCourses)]
        for i in prerequisites:
            deg[i[0]] += 1
            neigh[i[1]].append(i[0])
        q = deque([i for i in range(numCourses) if deg[i]==0])
        order =[]
        while q:
            u = q.popleft()
            order.append(u)
            for i in neigh[u]:
                deg[i] -= 1
                if deg[i] == 0:
                    q.append(i)
        if len(order) == numCourses:
            return order
        else:
            return []
```

<img width="877" height="537" alt="image" src="https://github.com/user-attachments/assets/8862c939-ac1d-48fc-8213-1aaee2103dae" />
