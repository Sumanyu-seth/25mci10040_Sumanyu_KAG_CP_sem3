```py
class Solution:
    def maxDistance(self, A, n):
        A.sort()
        L    = len(A)
        lo   = 1
        hi   = (A[-1]-A[0])//(n-1)
        best = 1
        n   -= 1
        def valid(mid):
            prev = A[0]
            i    = 0
            for j in range(n):
                d = prev + mid
                while i<L and A[i]<d:
                    i += 1
                if i==L:
                    return False
                prev = A[i]
            return True
        
        while lo<=hi:
            mid = (lo+hi) >> 1
            if valid(mid):
                best = mid
                lo   = mid + 1
            else:
                hi = mid - 1
        
        return best
  ```

<img width="886" height="532" alt="image" src="https://github.com/user-attachments/assets/db076f98-7542-404e-a451-36ea47344116" />
