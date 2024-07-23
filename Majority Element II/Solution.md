### Table of Contents

| S No. | Approach                                                          | Time Complexity | Space Complexity | Result  |
| ----- | ----------------------------------------------------------------- | --------------- | ---------------- | ------- |
| 1     | [Brute Force](#Brute-Force)                                       | O(N^2)          | O(N^2)           | TLE     |
| 2     | [Using Recursion](#Using-Recursion)                               | O(N*log(N))     | O(log(N))        | Success |
| 3     | [Using Sorting](#Using-Sorting)                                   | O(N*log(N))     | O(1)             | Success |
| 4     | [Using HasMap](#Using-HasMap)                                     | O(N)            | O(N)             | Success |
| 5     | [Using Moore’s Voting Algorithm](#Using-Moore’s-Voting-Algorithm) | O(N)            | O(1)             | Success |

### <h2>Brute Force</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        res, n = [], len(nums)
        if (n == 1 or n == 2):
            return list(set(nums))
        for i in range(n):
            c = 1
            for j in range(i+1, n):
                if (nums[i] == nums[j]):
                    c += 1
                    if (c > n//3):
                        res.append(nums[i])
                        break
        return list(set(res))
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using Recursion</h2>

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using Sorting</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        n = len(nums)
        if (n == 1 or n == 2):
            return list(set(nums))
        nums.sort()
        res = []
        i = 0
        while(i < n):
            count = 1
            while(i + 1 < n and nums[i] == nums[i + 1]):
                count += 1
                i += 1
            if(count > n // 3):
                res.append(nums[i])
            i += 1
        return res
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using HasMap</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        res = []
        hashMap, n = {}, len(nums)
        if (n == 1 or n == 2):
            return list(set(nums))
        for i in nums:
            if (i not in hashMap):
                hashMap[i] = 1
            else:
                hashMap[i] += 1
        for i in hashMap:
            if (hashMap[i] > n//3 and i not in res):
                res.append(i)
        return res
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Using Moore’s Voting Algorithm</h2>

```py
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        n = len(nums)
        if (n == 1 or n == 2):
            return list(set(nums))
        count1, count2, element1, element2 = 0, 0, None, None
        for i in range(n):
            if (count1 == 0 and nums[i] != element2):
                element1 = nums[i]
                count1 = 1
            elif (count2 == 0 and nums[i] != element1):
                element2 = nums[i]
                count2 = 1
            elif (element1 == nums[i]):
                count1 += 1
            elif (element2 == nums[i]):
                count2 += 1
            else:
                count1 -= 1
                count2 -= 1
        count1, count2 = 0, 0
        res = []
        for i in range(n):
            if (element1 == nums[i]):
                count1 += 1
            if (element2 == nums[i]):
                count2 += 1
        if (count1 > n//3):
            res.append(element1)
        if (count2 > n//3):
            res.append(element2)
        return res
```

**[⬆ Back to Top](#table-of-contents)**


<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/majority-element/description/">169. Majority Element</a>
2. <a href="https://leetcode.com/problems/most-frequent-even-element/description/">2404. Most Frequent Even Element</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
