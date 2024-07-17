### Table of Contents

| S No. | Approach                                                              | Time Complexity | Space Complexity | Result                           |
| ----- | --------------------------------------------------------------------- | --------------- | ---------------- | -------------------------------- |
| 1     | [Iterative Approach](#Iterative-Approach)                             | O(N)            | O(1)             | TLE - 291 / 306 testcases passed |
| 2     | [Recursive Approach (Naive)](#Recursive-Approach-(Naive))             | O(N)            | O(n)             | TLE - 291 / 306 testcases passed |
| 3     | [Fast Power Algorithm (Iterative)](#Fast-Power-Algorithm-(Iterative)) | O(log(N))       | O(1)             | Accepted                         |
| 4     | [Fast Power Algorithm (Recursive)](#Fast-Power-Algorithm-(Recursive)) | O(log(N))       | O(log(N))        | Accepted                         |

### <h2>Iterative Approach</h2>

```py
class Solution:
    def myPow(self, x: float, n: int) -> float:
        if(n == 0):
            return 1.0
        elif(n < 0):
            x = 1/x
            n = -n
        result = 1.0
        for i in range(n):
            result *= x
        return result
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Recursive Approach (Naive)</h2>

```py
class Solution:
    def myPow(self, x: float, n: int) -> float:
        if(n == 0):
            return 1.0
        elif(n < 0):
            return 1 / self.myPow(x, -n)
        return x * self.myPow(x, n - 1)
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Fast Power Algorithm (Iterative)</h2>

```py
class Solution:
    def myPow(self, x: float, n: int) -> float:
        if(n == 0):
            return 1.0
        elif(n < 0):
            x = 1/x
            n = -n
        result = 1.0
        currProduct = x
        while(n > 0):
            if(n % 2 == 1):
                result *= currProduct
            currProduct *= currProduct
            n //= 2
        return result
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Fast Power Algorithm (Recursive)</h2>

```py
class Solution:
    def myPow(self, x: float, n: int) -> float:
        def recusion(x: float, n: int) -> float:
            if(n == 0):
                return 1.0
            half = recusion(x, n // 2)
            if(n % 2 == 1):
                return half * half * x
            else:
                return half * half

        if(n < 0):
            x = 1 / x
            n = -n
        return recusion(x, n)
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/sqrtx/">69. Sqrt(x)</a>
2. <a href="https://leetcode.com/problems/super-pow/">372. Super Pow</a>
3. <a href="https://leetcode.com/problems/count-collisions-of-monkeys-on-a-polygon/description/">2550. Count Collisions of Monkeys on a Polygon</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
