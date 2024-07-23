### Table of Contents

| S No. | Approach                                                                      | Time Complexity | Space Complexity | Result  |
| ----- | ----------------------------------------------------------------------------- | --------------- | ---------------- | ------- |
| 1     | [Brute Force Approach Using Recursion](#Brute-Force-Approach-Using-Recursion) | O(2 ^ N)        | O(M + N)         | TLE     |
| 2     | [Using Memoization](#Using-Memoization)                                       | O(M * N)        | O(M * N)         | Success |
| 3     | [Using DP](#Using-DP)                                                         | O(M * N)        | O(M * N)         | Success |
| 4     | [Using DP Space Optimized](#Using-DP-Space-Optimized)                         | O(M * N)        | O(N)             | Success |
| 5     | [Using Combinatorics](#Using-Combinatorics)                                   | O(M)            | O(1)             | Success |

### <h2>Brute Force Approach Using Recursion</h2>

```py
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        if(m == 1 or n == 1):
            return 1
        return self.uniquePaths(m, n - 1) + self.uniquePaths(m - 1, n)
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using Memoization</h2>

```py
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        memo = {}
        def dp(i, j):
            if(i == m - 1 and j == n - 1): # Base case: when we reach the bottom-right corner
                return 1
            if(i >= m or j >= n): # If out of bounds
                return 0
            if((i, j) in memo): # Check if the result is already computed
                return memo[(i, j)]
            memo[(i, j)] = dp(i + 1, j) + dp(i, j + 1) # Recursive computation with memoization
            return memo[(i, j)]
        return dp(0, 0)
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using DP</h2>

```py
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        res = [[0 for i in range(n)] for j in range(m)]
        for i in range(m):
            res[i][0] = 1
        for i in range(n):
            res[0][i] = 1
        for i in range(1, m):
            for j in range(1, n):
                res[i][j] = res[i-1][j] + res[i][j-1]
        return res[m-1][n-1]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using DP Space Optimized</h2>

```py
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        res = [1 for i in range(n)]
        for i in range(m - 1):
            for j in range(1, n):
                res[j] += res[j - 1]
        return res[n - 1]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using Combinatorics</h2>

**calculate = (m + n-2)! / (n-1)! (m-1)!**

```py
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        v1, v2, v3 = 1, 1, 1
        for i in range(m+n-2, 0, -1):
            v1 *= i
        for i in range(n-1, 0, -1):
            v2 *= i
        for i in range(m-1, 0, -1):
            v3 *= i
        return v1//(v2*v3)
```
**OR**
```py
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        path = 1
        for i in range(n, (m + n - 1)):
            path *= i
            path //= (i - n + 1)
        return path
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/unique-paths-ii/description/">63. Unique Paths II</a>
2. <a href="https://leetcode.com/problems/minimum-path-sum/description/">64. Minimum Path Sum</a>
3. <a href="https://leetcode.com/problems/dungeon-game/description/">174. Dungeon Game</a>
4. <a href="https://leetcode.com/problems/minimum-path-cost-in-a-grid/description/">2304. Minimum Path Cost in a Grid</a>
5. <a href="https://leetcode.com/problems/minimum-cost-homecoming-of-a-robot-in-a-grid/description/">2087. Minimum Cost Homecoming of a Robot in a Grid</a>
6. <a href="https://leetcode.com/problems/number-of-ways-to-reach-a-position-after-exactly-k-steps/description/">2400. Number of Ways to Reach a Position After Exactly k Steps</a>
7. <a href="https://leetcode.com/problems/paths-in-matrix-whose-sum-is-divisible-by-k/description/">2435. Paths in Matrix Whose Sum Is Divisible by K</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
