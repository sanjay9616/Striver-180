### Table of Contents

| S No. | Approach                                      | Time Complexity | Space Complexity | Result   |
| ----- | --------------------------------------------- | --------------- | ---------------- | -------- |
| 1     | [Brute Force](#Brute-Force)                   | O(M∗N∗(M+N))    | O(1)             | Accepted |
| 2     | [Brute Force Opimized](#Brute-Force-Opimized) | O(M∗N)          | O(M+N)           | Accepted |
| 3     | [Opimized](#Opimized)                         | O(M∗N)          | O(1)             | Accepted |

### <h2>Brute Force</h2>

```py
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m, n = len(matrix), len(matrix[0])
        for i in range(m):
            for j in range(n):
                if(matrix[i][j] == 0):
                    for k in range(m):
                        if(matrix[k][j] != 0):
                            matrix[k][j] = None
                    for k in range(n):
                        if(matrix[i][k] != 0):
                            matrix[i][k] = None
        for i in range(m):
            for j in range(n):
                if(matrix[i][j] == None):
                    matrix[i][j] = 0
        return matrix
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Brute Force Opimized</h2>

```py
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m, n = len(matrix), len(matrix[0])
        row, col = [0]*m, [0]*n
        for i in range(m):
            for j in range(n):
                if(matrix[i][j] == 0):
                    row[i] = col[j] = 1
        for i in range(m):
            for j in range(n):
                if(row[i] == 1 or col[j] == 1):
                    matrix[i][j] = 0
        return matrix
```

### <h2>Optimized</h2>

```py
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m, n = len(matrix), len(matrix[0])
        col0 = 1
        for i in range(m):
            for j in range(n):
                if(matrix[i][j] == 0):
                    matrix[i][0] = 0
                    if(j == 0):
                        col0 = 0
                    else:
                        matrix[0][j] = 0
        for i in range(1, m):
            for j in range(1, n):
                if (matrix[i][0] == 0 or matrix[0][j] == 0):
                    matrix[i][j] = 0
        if (matrix[0][0] == 0):
            for i in range(n):
                matrix[0][i] = 0
        if (col0 == 0):
            for i in range(m):
                matrix[i][0] = 0
        return matrix
```

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/game-of-life/description/">289. Game of Life</a>
2. <a href="https://leetcode.com/problems/number-of-laser-beams-in-a-bank/description/">2125. Number of Laser Beams in a Bank</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
