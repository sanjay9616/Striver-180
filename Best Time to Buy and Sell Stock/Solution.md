### Table of Contents

| S No. | Approach                                                                                              | Time Complexity | Space Complexity | Result   |
| ----- | ----------------------------------------------------------------------------------------------------- | --------------- | ---------------- | -------- |
| 1     | [Brute Force](#Brute-Force)                                                                           | O(N^2)          | O(1)             | TLE      |
| 2     | [Brute Force Using Python Function (combinations)](#Brute-Force-Using-Python-Function-(combinations)) | O(N^2)          | O(1)             | TLE      |
| 3     | [Greedy Approach](#Greedy-Approach)                                                                   | O(N)            | O(1)             | Accepted |
| 4     | [Recursion and Memoization](#Recursion-and-Memoization)                                               | O(2^N)          | O(N)             | TLE      |
| 5     | [Dynamic Programming](#Dynamic-Programming)                                                           | O(N)            | O(N)             | TLE      |

### <h2>Brute Force</h2>

```py
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        maxProfit = 0
        for i in range(len(prices)):
            for j in range(i+1, len(prices)):
                if (prices[j]-prices[i] > maxProfit):
                    maxProfit = prices[j]-prices[i]
        return maxProfit
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Brute Force Using Python Function (combinations)</h2>

```py
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        maxProfit = 0
        from itertools import combinations
        for p in combinations(prices, 2):
            maxProfit = max(maxProfit, p[1]-p[0])
        return maxProfit
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Greedy Approach</h2>

```py
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        maxProfit, buy = 0, prices[0]
        for i in range(len(prices)):
            if (buy > prices[i]):
                buy = prices[i]
            elif (prices[i] - buy > maxProfit):
                maxProfit = prices[i] - buy
        return maxProfit
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Recursion and Memoization</h2>

**[⬆ Back to Top](#table-of-contents)**


<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/maximum-subarray/description/">53. Maximum Subarray</a>
2. <a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/">122. Best Time to Buy and Sell Stock II</a>
3. <a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/">123. Best Time to Buy and Sell Stock III</a>
4. <a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/">188. Best Time to Buy and Sell Stock IV</a>
5. <a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/">309. Best Time to Buy and Sell Stock with Cooldown</a>
6. <a href="https://leetcode.com/problems/sum-of-beauty-in-the-array/description/">2012. Sum of Beauty in the Array</a>
7. <a href="https://leetcode.com/problems/maximum-difference-between-increasing-elements/description/">2016. Maximum Difference Between Increasing Elements</a>


<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
