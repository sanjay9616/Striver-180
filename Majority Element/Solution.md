### Table of Contents

| S No. | Approach                                                      | Time Complexity     | Space Complexity | Result   |
| ----- | ------------------------------------------------------------- | ------------------- | ---------------- | -------- |
| 1     | [Brute Force](#Brute-Force)                                   | O(N^2)              | O(1)             | TLE      |
| 2     | [Sorting](#Sorting)                                           | O(N*log(N))         | O(1)             | Accepted |
| 3     | [Hash Map](#Hash-Map)                                         | O(N)                | O(N)             | Accepted |
| 4     | [Boyer-Moore Voting Algorithm](#Boyer-Moore-Voting-Algorithm) | O(N)                | O(1)             | Accepted |
| 5     | [Divide and Conquer](#Divide-and-Conquer)                     | O(N*log(N))         | O(log(N))        | Accepted |
| 6     | [Randomization](#Randomization)                               | O(N) to O(Infinite) | O(1)             | TLE      |

### <h2>Brute Force</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        n = len(nums)
        if(n==1):
            return nums[0]
        for i in range(n):
            c=1
            for j in range(i+1, n):
                if(nums[i]==nums[j]):
                    c+=1
                    if(c > n//2):
                        return nums[i]
        return -1
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Sorting</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        nums.sort()
        return nums[len(nums)//2]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Hash Map</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        counts = {}
        for num in nums:
            if num in counts:
                counts[num] += 1
            else:
                counts[num] = 1
            if(counts[num] > len(nums) // 2):
                return num
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Boyer-Moore Voting Algorithm</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        count, candidate = 0, None
        for i in nums:
            if(count == 0):
                candidate = i
            if(i == candidate):
                count += 1
            else:
                count -= 1
        count = 0
        for i in nums:
            if(i == candidate):
                count += 1
        if(count > len(nums) // 2):
            return candidate
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Divide and Conquer</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        def countElement(arr, num):
            count = 0
            for i in arr:
                if i == num:
                    count += 1
            return count
        def findMajority(arr, low, high):
            if low == high: # has 1 length
                return arr[low]
            mid = (low + high) // 2
            left = findMajority(arr, low, mid)
            right = findMajority(arr, mid+1, high)
            if left == right: #has 2 length
                return left
            left_count = countElement(arr[low:high+1], left)
            right_count = countElement(arr[low:high+1], right)
            if left_count > (high-low+1) // 2:
                return left
            if right_count > (high-low+1) // 2:
                return right
            return -1
        n = len(nums)
        return findMajority(nums, 0, n-1)
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Randomization</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        import random
        while True:
            candidate = random.choice(nums)
            if nums.count(candidate) > len(nums) // 2:
                return candidate
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/sqrtx/">69. Sqrt(x)</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
