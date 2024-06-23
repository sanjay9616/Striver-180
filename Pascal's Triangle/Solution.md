### Table of Contents

| S No. | Approach              | Time Complexity | Space Complexity | Result   |
| ----- | --------------------- | --------------- | ---------------- | -------- |
| 1     | [Solution](#Solution) | O(N^2)          | O(N)             | Accepted |
|       |

### <h2>Solution</h2>

```py
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        if(numRows==0):
            return []
        l=[[1]]
        for i in range(numRows-1):
            l.append([sum(i) for i in zip(l[-1]+[0], [0]+l[-1])])
        return l
```
```py
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        if(numRows==0):
            return []
        l=[[1]]
        for i in range(numRows-1):
            a=l[-1]+[0]
            b=[0]+l[-1]
            l1=[]
            for j in range(len(a)):
                l1.append(a[j]+b[j])
            l.append(l1)
            l1=[]
        return l
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/pascals-triangle-ii/submissions/1076612080/">289. Game of Life</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
