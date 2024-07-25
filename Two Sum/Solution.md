### Table of Contents

| S No. | Approach                        | Time Complexity | Space Complexity | Result   |
| ----- | ------------------------------- | --------------- | ---------------- | -------- |
| 1     | [Brute Force](#Brute-Force)     | O(N^2)          | O(1)             | TLE      |
| 2     | [Using Sort](#Using-Sort)       | O(N^2)          | O(1)             | Accepted |
| 3     | [Using HashMap](#Using-HashMap) | O(N)            | O(N)             | Accepted |

### <h2>Brute Force</h2>

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if(nums[i] + nums[j] == target):
                    return [i, j]
        return -1
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using Sort</h2>

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        l1 = []
        for i in range(len(nums)):
            l1.append([nums[i], i])
        l1.sort()
        i, j = 0, len(nums)-1
        while(i < j):
            sum = l1[i][0] + l1[j][0]
            if(sum == target):
                return [l1[i][1], l1[j][1]]
            if(target > sum):
                i += 1
            else:
                j -= 1
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using HashMap</h2>

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hasMap = {}
        for i in range(len(nums)):
            if(target - nums[i] not in hasMap):
                hasMap[nums[i]] = i
            else:
                return [hasMap[target - nums[i]], i]
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/3sum/">15. 3Sum</a>
1. <a href="https://leetcode.com/problems/4sum/">18. 4Sum</a>
1. <a href="https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/">167. Two Sum II - Input Array Is Sorted</a>
1. <a href="https://leetcode.com/problems/subarray-sum-equals-k/description/">560. Subarray Sum Equals K</a>
1. <a href="https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/">653. Two Sum IV - Input is a BST</a>
1. <a href="https://leetcode.com/problems/max-number-of-k-sum-pairs/description/">1679. Max Number of K-Sum Pairs</a>
1. <a href="https://leetcode.com/problems/count-good-meals/description/">1711. Count Good Meals</a>
1. <a href="https://leetcode.com/problems/count-number-of-pairs-with-absolute-difference-k/description/">2006. Count Number of Pairs With Absolute Difference K</a>
1. <a href="https://leetcode.com/problems/number-of-pairs-of-strings-with-concatenation-equal-to-target/description/">2023. Number of Pairs of Strings With Concatenation Equal to Target</a>
1. <a href="https://leetcode.com/problems/find-all-k-distant-indices-in-an-array/description/">2200. Find All K-Distant Indices in an Array</a>
1. <a href="https://leetcode.com/problems/first-letter-to-appear-twice/description/">2351. First Letter to Appear Twice</a>
1. <a href="https://leetcode.com/problems/number-of-excellent-pairs/description/">2354. Number of Excellent Pairs</a>
1. <a href="https://leetcode.com/problems/node-with-highest-edge-score/description/">2374. Node With Highest Edge Score</a>
1. <a href="https://leetcode.com/problems/check-distances-between-same-letters/description/">2399. Check Distances Between Same Letters</a>
1. <a href="https://leetcode.com/problems/find-subarrays-with-equal-sum/description/">2395. Find Subarrays With Equal Sum</a>
1. <a href="https://leetcode.com/problems/largest-positive-integer-that-exists-with-its-negative/description/">2441. Largest Positive Integer That Exists With Its Negative</a>
1. <a href="https://leetcode.com/problems/number-of-distinct-averages/description/">2465. Number of Distinct Averages</a>
2. <a href="https://leetcode.com/problems/count-pairs-whose-sum-is-less-than-target/description/">2824. Count Pairs Whose Sum is Less than Target</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
