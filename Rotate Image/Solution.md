### Table of Contents

| S No. | Approach                                                                          | Time Complexity | Space Complexity | Result   |
| ----- | --------------------------------------------------------------------------------- | --------------- | ---------------- | -------- |
| 1     | [Brute Force](#Brute-Force)                                                       | O(N^2)          | O(N^2)           | Accepted |
| 2     | [Transpose then Reverse individual rows](#Transpose-then-Reverse-individual-rows) | O(N^2)          | O(1)             | Accepted |
| 3     | [Rotate Cycle Wise](#Rotate-Cycle-Wise)                                           | O(N^2)          | O(1)             | Accepted |

### <h2>Brute Force</h2>

```py
# Transpose -> Reverse
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        n = len(matrix)
        res = [[0 for _ in range(n)] for _ in range(n)]
        for i in range(n):
            for j in range(n):
                res[j][n - i - 1] = matrix[i][j]
        matrix[:] = res
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Transpose then Reverse individual rows</h2>

```py
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        n = len(matrix)

        def Transpose(matrix): # Only Works on Square matrix n * n
            for i in range(n):
                for j in range(i+1, n):
                    matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
            return matrix

        def reverseEachRow(matrix):
            for i in range(n):
                for j in range(n//2):
                    matrix[i][j], matrix[i][n- 1 - j] = matrix[i][n - 1 - j], matrix[i][j]
        reverseEachRow(Transpose(matrix))
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Rotate Cycle Wise</h2>

```py
'''
Print the elements of the cycle in a clockwise direction i.e. An N x N matrix will have floor(N/2) square cycles.

For each square cycle, we swap the elements involved with the corresponding cell in the matrix in the clockwise direction. We just need a temporary variable for this.
'''

class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        n = len(matrix)
        for i in range(n // 2):
            for j in range(i, n - i - 1):
                temp = matrix[i][j]
                matrix[i][j] = matrix[n - 1 - j][i]
                matrix[n - 1 - j][i] = matrix[n - 1 - i][n - 1 - j]
                matrix[n - 1 - i][n - 1 - j] = matrix[j][n - 1 - i]
                matrix[j][n - 1 - i] = temp
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/determine-whether-matrix-can-be-obtained-by-rotation/description/">1886. Determine Whether Matrix Can Be Obtained By Rotation</a>



<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
