```py
import heapq
from typing import List

class Solution:
    def minimumTime(self, n: int, relations: List[List[int]], time: List[int]) -> int:
        adj = [[] for _ in range(n)]
        indegree = [0] * n
        
        for u, v in relations:
            u -= 1
            v -= 1
            adj[u].append(v)
            indegree[v] += 1
        
        heap = []
        for i in range(n):
            if indegree[i] == 0:
                heapq.heappush(heap, (time[i], i))
        
        max_time = 0
        
        while heap:
            finish_time, node = heapq.heappop(heap)
            max_time = max(max_time, finish_time)
            
            for neighbor in adj[node]:
                indegree[neighbor] -= 1
                if indegree[neighbor] == 0:
                    heapq.heappush(heap, (finish_time + time[neighbor], neighbor))
        
        return max_time
```
<img width="791" height="656" alt="image" src="https://github.com/user-attachments/assets/9395a866-1c93-4cd2-b1ea-0733dea93824" />
