### Table of Contents

| S No. | Approach                                                                                                               | Time Complexity | Space Complexity | Result   |
| ----- | ---------------------------------------------------------------------------------------------------------------------- | --------------- | ---------------- | -------- |
| 1     | [Brute Force Approach using Linear Search](#Brute-Force-Approach-using-Linear-Search)                                  | O(M*N)          | O(1)             | Accepted |
| 1     | [Using Binary Search](#Using-Binary-Search)                                                                            | O(M)*log(N)     | O(1)             | Accepted |
| 1     | [Flatten 2d matrix into 1d array then apply Binary Search](#UFlatten-2d-matrix-into-1d-array-then-apply-Binary-Search) | O(M)+log(N)     | O(1)             | Accepted |

### <h2>Brute Force Approach using Linear Search</h2>

```py
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                if (matrix[i][j] == target):
                    return True
        return False
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Brute Force Approach using Linear Search</h2>

```py
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        def binarySearch(arr, x):
            l, r = 0, len(arr) - 1
            while l <= r:
                mid = l + (r - l) // 2
                if arr[mid] == x:
                    return True
                elif arr[mid] < x:
                    l = mid + 1
                else:
                    r = mid - 1
            return False
        m, n = len(matrix), len(matrix[0])
        for i in range(m):
            if (matrix[i][0] <= target and target <= matrix[i][n - 1]):
                return binarySearch(matrix[i], target)
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Flatten 2d matrix into 1d array then apply Binary Search</h2>

```py
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        m, n = len(matrix), len(matrix[0])
        low, high = 0, m * n - 1
        while(low <= high):
            mid = (low + high) // 2
            row, col = mid // n, mid % n
            if(matrix[row][col] == target):
                return True
            elif(matrix[row][col] < target):
                low = mid + 1
            elif(matrix[row][col] > target):
                high = mid - 1
        return False
```

**[⬆ Back to Top](#table-of-contents)**



<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/search-a-2d-matrix-ii/description/">240. Search a 2D Matrix II</a>
2. <a href="https://leetcode.com/problems/split-message-based-on-limit/description/">2468. Split Message Based on Limit</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
