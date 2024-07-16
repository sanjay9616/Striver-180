### Table of Contents

| S No. | Approach                                | Time Complexity | Space Complexity | Result   |
| ----- | --------------------------------------- | --------------- | ---------------- | -------- |
| 1     | [Brute Force](#Brute-Force)             | O(N^2)          | O(1)             | Accepted |
| 2     | [Using Sum Formula](#Using-Sum-Formula) | O(1)            | O(1)             | Accepted |
| 3     | [Using XOR](#Using-XOR)                 | O(N)            | O(1)             | Accepted |
| 4     | [Using a Set](#Using-a-Set)             | O(N)            | O(1)             | Accepted |

### <h2>Brute Force</h2>

```py
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        for i in range(len(nums)+1):
            if(i not in nums):
                return i
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using Sum Formula</h2>

```py
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        expected_sum = n * (n + 1) // 2
        actual_sum = sum(nums)
        return expected_sum - actual_sum
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using XOR</h2>

```py
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        missing = n  # Start with n (the missing number might be n)
        for i in range(n):
            missing ^= i ^ nums[i]
        return missing
```
**OR**
```py
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        # Approach 2: Using xor
        missing = 0
        for num in nums:
            missing ^= num
        for i in range(len(nums) + 1):
            missing ^= i
        return missing
        '''
        In this approach,
        you use bitwise XOR operation to find the missing number.
        XOR operation on a number with itself results in 0.
        So, if you XOR all the numbers from 0 to n
        and
        all the numbers in the array, the result will be the missing number.
        XOR = (1 ^ 3  ^ 5 ^ 6) ^ (1 ^ 2 ^ 3 ^ 4 ^ 5 ^ 6) = 4
        '''
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using a Set</h2>

```py
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        num_set = set(nums)
        n = len(nums)
        for i in range(n + 1):
            if i not in num_set:
                return i
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/first-missing-positive/description/">41. First Missing Positive</a>
2. <a href="https://leetcode.com/problems/single-number/description/">136. Single Number</a>
3. <a href="https://leetcode.com/problems/find-the-duplicate-number/description/">287. Find the Duplicate Number</a>
4. <a href="https://leetcode.com/problems/couples-holding-hands/description/">765. Couples Holding Hands</a>
5. <a href="https://leetcode.com/problems/find-unique-binary-string/description/">1980. Find Unique Binary String</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
