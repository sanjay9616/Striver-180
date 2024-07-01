<h2><a href="https://github.com/sanjay9616/data-structure-and-alogrithms/blob/master/Sorting/README.md">Different Types of Sorting Algorithms</a></h2>

**Time Complexity O(N<sup>2</sup>)**

| Algorithm      | Time Complexity  | Space Complexity (Worst Case) |
| -------------- | ---------------- | ----------------------------- |
| Bubble Sort    | O(N<sup>2</sup>) | O(1)                          |
| Selection Sort | O(N<sup>2</sup>) | O(1)                          |
| Insertion Sort | O(N<sup>2</sup>) | O(1)                          |

**Approach 2: Time ComplexityO(N * K)**

| Algorithm  | Time Complexity | Space Complexity (Worst Case) |
| ---------- | --------------- | ----------------------------- |
| Radix Sort | O(N * K)        | O(N + K)                      |

**Time Complexity O(N log N)**

| Algorithm  | Time Complexity               | Space Complexity (Worst Case) |
| ---------- | ----------------------------- | ----------------------------- |
| Merge Sort | O(N log N)                    | O(N)                          |
| Quick Sort | O(N log N) / O(N<sup>2</sup>) | O(N)                          |
| Heap Sort  | O(N log N)                    | O(1)                          |

**Time Complexity O(N + K)**

| Algorithm     | Time Complexity             | Space Complexity (Worst Case) |
| ------------- | --------------------------- | ----------------------------- |
| Counting Sort | O(N + K)                    | O(K)                          |
| Bucket Sort   | O(N + K) / O(N<sup>2</sup>) | O(N)                          |

### Table of Contents

| S No. | Approach                                                                      | Time Complexity | Space Complexity | Result   |
| ----- | ----------------------------------------------------------------------------- | --------------- | ---------------- | -------- |
| 1     | [Count Elements](#Count-Elements)                                             | O(2 * N)        | O(1)             | Accepted |
| 2     | [Single Scan - Three-way partitioning](#Single-Scan---Three-way-partitioning) | O(N)            | O(1)             | Accepted |

### <h2>Count Elements</h2>

The basic idea that comes to mind is to simply count the number of 0’s, 1’s, and 2’s. Then, place all 0’s at the beginning of the array followed by 1’s and 2's.

```py
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        zero, one, two = 0, 0, 0
        for i in nums:
            if (i == 0):
                zero += 1
            elif (i == 1):
                one += 1
            elif (i == 2):
                two += 1
        i = 0
        while (zero > 0):
            nums[i] = 0
            i += 1
            zero -= 1
        while (one > 0):
            nums[i] = 1
            i += 1
            one -= 1
        while (two > 0):
            nums[i] = 2
            i += 1
            two -= 1
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Single Scan - Three-way partitioning</h2>

The critical question is: can we solve the problem in a single traversal of the array? We have only three unique elements in the input, so can we use an idea similar to the partition process of the quicksort

```py
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        low, mid, high = 0, 0, len(nums) - 1
        while(mid <= high):
            if(nums[mid] == 0):
                nums[low], nums[mid] = nums[mid], nums[low]
                low += 1
                mid += 1
            elif(nums[mid] == 1):
                mid += 1
            elif(nums[mid] == 2):
                nums[mid], nums[high] = nums[high], nums[mid]
                high -= 1
```

**[⬆ Back to Top](#table-of-contents)**

<h2>Similar Questions</h2>

1. <a href="https://leetcode.com/problems/sort-list/description/">148. Sort List</a>
2. <a href="https://leetcode.com/problems/wiggle-sort-ii/description/">324. Wiggle Sort II</a>

<h2><a href="https://github.com/sanjay9616/Striver-180/blob/master/README.md"> 🔙 Back</a></h2>
