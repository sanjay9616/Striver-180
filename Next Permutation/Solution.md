### Table of Contents

| S No. | Approach                    | Time Complexity | Space Complexity | Result   |
| ----- | --------------------------- | --------------- | ---------------- | -------- |
| 1     | [Brute Force](#Brute-Force) | O(N)            | O(1)             | Accepted |

### <h2>Brute Force</h2>

```py
class Solution:
    def nextPermutation(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        inx = -1
        for i in range(len(nums)-2, -1, -1):
            if(nums[i] < nums[i+1]):
                inx = i
                break
        if(inx == -1):
            nums[:] = nums[:][::-1]
        else:
            m = nums[inx+1]
            mInx = inx+1
            for i in range(inx+1, len(nums)):
                if(m >= nums[i] and nums[inx] < nums[i]):
                    m = nums[i]
                    mInx = i
            nums[inx], nums[mInx] = nums[mInx], nums[inx]
            nums[:] = nums[:inx+1]+nums[inx+1:][::-1]
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/permutations/description/">46. Permutations</a>
2. <a href="https://leetcode.com/problems/permutations-ii/description/">Permutations II</a>
3. <a href="https://leetcode.com/problems/permutation-sequence/description/">60. Permutation Sequence</a>
4. <a href="https://leetcode.com/problems/minimum-adjacent-swaps-to-reach-the-kth-smallest-number/description/">1850. Minimum Adjacent Swaps to Reach the Kth Smallest Number</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
