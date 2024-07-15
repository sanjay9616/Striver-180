### Table of Contents

| S No. | Approach                                                                                  | Time Complexity | Space Complexity | Result  |
| ----- | ----------------------------------------------------------------------------------------- | --------------- | ---------------- | ------- |
| 1     | [Brute Force Approach using Linear Search](#Brute-Force-Approach-using-Linear-Search)     | O(N^2)          | O(1)             | TLE     |
| 2     | [First sort Array and then compare adjucent](#First-sort-Array-and-then-compare-adjucent) | O(N*log(N))     | O(1)             | Success |
| 3     | [Using HashMap](#Using-HashMap)                                                           | O(N)            | O(N)             | Success |
| 4     | [Linked List cycle method](#Linked-List-cycle-method)                                     | O(N)            | O(1)             | Success |

### <h2>Brute Force Approach using Linear Search</h2>

```py
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        for i in range(len(nums)):
            c = 0
            for j in range(i+1, len(nums)):
                if (nums[i] == nums[j]):
                    return nums[i]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>First sort Array and then compare adjucent</h2>

```py
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        nums.sort()
        for i in range(len(nums)-1):
            if (nums[i] == nums[i+1]):
                return nums[i]
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using HasMap</h2>

```py
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        hashMap = {}
        for i in nums:
            if (i not in hashMap):
                hashMap[i] = 1
            else:
                hashMap[i] += 1
        for i in hashMap:
            if (hashMap[i] >= 2):
                return i
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Linked List cycle method</h2>

```py
# taking 482 ms
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        slow, fast = nums[0], nums[0]
        while(True):
            slow = nums[slow]
            fast = nums[nums[fast]]
            if(slow == fast):
                break
        slow = nums[0]
        while(slow != fast):
            slow = nums[slow]
            fast = nums[fast]
        return slow
```
**OR**
```py
# Similar to Question 142. Linked List Cycle II = taking 468 ms
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        slow, fast = nums[0], nums[0]
        while(nums[fast] and nums[nums[fast]]):
            slow = nums[slow]
            fast = nums[nums[fast]]
            if(slow == fast):
                slow = nums[0]
                while(slow != fast):
                    slow = nums[slow]
                    fast = nums[fast]
                return slow
        return -1
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/first-missing-positive/description/">41. First Missing Positive</a>
2. <a href="https://leetcode.com/problems/single-number/description/">136. Single Number</a>
3. <a href="https://leetcode.com/problems/linked-list-cycle-ii/description/">142. Linked List Cycle II</a>
4. <a href="https://leetcode.com/problems/missing-number/description/">268. Missing Number</a>
5. <a href="https://leetcode.com/problems/set-mismatch/description/">645. Set Mismatch</a>


<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
