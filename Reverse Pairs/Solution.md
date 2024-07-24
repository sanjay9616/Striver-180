### Table of Contents

| S No. | Approach                              | Time Complexity | Space Complexity | Result |
| ----- | ------------------------------------- | --------------- | ---------------- | ------ |
| 1     | [Brute Force](#Brute-Force)           | O(N^2)          | O(1)             | TLE    |
| 2     | [Using Merge Sort](#Using-Merge-Sort) | O(N * log(N))   | O(1)             | TLE    |

### <h2>Brute Force</h2>

```py
class Solution:
    def reversePairs(self, nums: List[int]) -> int:
        c =0
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if(nums[i] > nums[j]*2):
                    c += 1
        return c
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using Merge Sort</h2>

```py
class Solution:
    def reversePairs(self, nums: List[int]) -> int:
        def merge_sort(start, end):
            if start >= end:
                return 0
            mid = (start + end) // 2
            count = merge_sort(start, mid) + merge_sort(mid + 1, end)

            # Count the number of reverse pairs between two sorted halves
            i = start
            j = mid + 1
            while i <= mid and j <= end:
                if nums[i] > 2 * nums[j]:
                    count += mid - i + 1
                    j += 1
                else:
                    i += 1

            # Merge two sorted halves
            nums[start:end + 1] = sorted(nums[start:end + 1])

            return count

        return merge_sort(0, len(nums) - 1)
```
**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/count-of-smaller-numbers-after-self/">315. Count of Smaller Numbers After Self</a>
2. <a href="https://leetcode.com/problems/count-of-range-sum/">327. Count of Range Sum</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
