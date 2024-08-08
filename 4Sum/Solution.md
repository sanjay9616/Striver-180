### Table of Contents

| S No. | Approach                      | Time Complexity | Space Complexity | Result   |
| ----- | ----------------------------- | --------------- | ---------------- | -------- |
| 1     | [Most Optimal](#Most-Optimal) | O(N^3)          | O(1)             | Accepted |

### <h2>Most Optimal</h2>

```py
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        nums.sort()
        result, n = [], len(nums)
        for i in range(n):
            if(i > 0 and nums[i] == nums[i - 1]): # Skip duplicate for the first number
                continue
            for j in range(i + 1, n):
                if(j > i + 1 and nums[j] == nums[j - 1]): # Skip duplicate for the second number
                    continue
                left, right = j + 1, n - 1 # Two-pointer approach for the remaining two numbers
                while(left < right):
                    total = nums[i] + nums[j] + nums[left] + nums[right]
                    if(total == target):
                        result.append([nums[i], nums[j], nums[left], nums[right]])
                        while left < right and nums[left] == nums[left + 1]: # Skip duplicates for the third number
                            left += 1
                        while left < right and nums[right] == nums[right - 1]: # Skip duplicates for the fourth number
                            right -= 1
                        left += 1
                        right -= 1
                    elif total < target:
                        left += 1
                    else:
                        right -= 1
        return result
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/two-sum/description/">1. Two Sum</a>
2. <a href="https://leetcode.com/problems/3sum/description/">15. 3Sum</a>
3. <a href="https://leetcode.com/problems/4sum-ii/description/">454. 4Sum II</a>
4. <a href="https://leetcode.com/problems/count-special-quadruplets/description/">1995. Count Special Quadruplets</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
