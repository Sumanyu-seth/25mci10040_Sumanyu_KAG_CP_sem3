```py
class Solution:
    def constructRectangle(self, area: int) -> List[int]:
        for l in range(int(area**0.5), 0, -1):            
            if area % l == 0: 
                return [area // l, l]
```

<img width="912" height="652" alt="image" src="https://github.com/user-attachments/assets/ba87030b-7d02-477b-83d8-77354225d5f9" />
