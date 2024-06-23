### Table of Contents

| S No. | Approach                              | Time Complexity | Space Complexity | Result |
| ----- | ------------------------------------- | --------------- | ---------------- | ------ |
| 1     | [Brute Force](#Brute-Force)           | O(N^2)          | O(1)             | TLE    |
| 1     | [Kadane Algorithm](#Kadane-Algorithm) | O(N)            | O(1)             | Sucess |

### <h2>Brute Force</h2>

```py
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        M=float('-inf')
        for i in range(len(nums)):
            s=0
            for j in range(i,len(nums)):
                s+=nums[j]
                M=max(M,s)
        return M
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Kadane Algorithm</h2>

```py
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        maxSum, currSum = float('-inf'), 0
        for i in nums:
            currSum += i
            if(currSum > maxSum):
                maxSum = currSum
            if(currSum < 0):
                currSum = 0
        return maxSum
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/">121. Best Time to Buy and Sell Stock</a>
2. <a href="https://leetcode.com/problems/maximum-product-subarray/description/">152. Maximum Product Subarray</a>
3. <a href="https://leetcode.com/problems/degree-of-an-array/description/">697. Degree of an Array</a>
4. <a href="https://leetcode.com/problems/longest-turbulent-subarray/description/">978. Longest Turbulent Subarray</a>
5. <a href="https://leetcode.com/problems/maximum-score-of-spliced-array/description/">2321. Maximum Score Of Spliced Array</a>
6. <a href="https://leetcode.com/problems/maximum-absolute-sum-of-any-subarray/description/">1749. Maximum Absolute Sum of Any Subarray</a>
7. <a href="https://leetcode.com/problems/substring-with-largest-variance/description/">2272. Substring With Largest Variance</a>
8. <a href="https://leetcode.com/problems/count-subarrays-with-score-less-than-k/description/">2302. Count Subarrays With Score Less Than K</a>
9. <a href="https://leetcode.com/problems/maximum-value-of-a-string-in-an-array/description/">2496. Maximum Value of a String in an Array</a>
10. <a href="https://leetcode.com/problems/find-the-substring-with-maximum-cost/description/">2606. Find the Substring With Maximum Cost</a>
11. <a href="https://leetcode.com/problems/k-items-with-the-maximum-sum/description/">2600. K Items With the Maximum Sum</a>
12. <a href="https://leetcode.com/problems/maximum-good-subarray-sum/description/">3026. Maximum Good Subarray Sum</a>


<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
